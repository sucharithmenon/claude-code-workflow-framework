# Ruby on Rails CCWF Customization

## Customize Your .claude/commands/issue.md

Replace the testing section with:

```markdown
# TEST
- Use puppeteer via MCP to test the changes if you have made changes to the UI
- Write RSpec tests to describe the expected behavior of your code
- Write Rails system tests for full-stack features
- Run the full test suite: `bundle exec rspec`
- Run system tests: `bundle exec rails test:system`
- Run Rails security audit: `bundle audit`
- Run code quality checks: `bundle exec rubocop`
- If the tests are failing, fix them
- Ensure that all tests are passing before moving on to the next step
```

## Add to Your CLAUDE.md

```markdown
# Development Commands

## Rails Development
```bash
# Bundle management
bundle install                  # Install dependencies
bundle update                   # Update dependencies
bundle audit                    # Security audit

# Rails server and console
rails server                    # Start development server (http://localhost:3000)
rails console                   # Rails console
rails dbconsole                 # Database console

# Database
rails db:create                 # Create database
rails db:migrate                # Run migrations
rails db:seed                   # Seed database
rails db:reset                  # Drop, create, migrate, and seed
rails db:rollback               # Rollback last migration

# Code generation
rails generate model User name:string email:string
rails generate controller Users index show
rails generate migration AddIndexToUsers email:index

# Testing
bundle exec rspec               # Run RSpec tests
bundle exec rspec spec/models   # Run model tests only
rails test:system               # Run system tests
bundle exec guard               # Continuous testing

# Code quality
bundle exec rubocop             # Linting
bundle exec rubocop -a          # Auto-correct issues
bundle exec brakeman            # Security analysis
bundle exec rails_best_practices # Best practices check

# Assets and deployment
rails assets:precompile         # Precompile assets
rails credentials:edit          # Edit encrypted credentials
```

## Project Structure
```
app/
├── controllers/                # Application controllers
├── models/                     # ActiveRecord models
├── views/                      # View templates
├── helpers/                    # View helpers
├── mailers/                    # ActionMailer classes
├── jobs/                       # Background jobs
└── services/                   # Service objects
config/
├── routes.rb                   # Application routes
├── application.rb              # Application configuration
├── database.yml                # Database configuration
└── environments/               # Environment-specific configs
spec/                           # RSpec tests
├── models/
├── controllers/
├── features/                   # Feature specs
├── system/                     # System tests
└── support/                    # Test support files
```
```

## Example Infrastructure Issues for Rails

### 1. Set up Testing Framework
```markdown
## Summary
Configure RSpec, FactoryBot, and system testing with comprehensive test coverage

## Acceptance Criteria
- [ ] RSpec installed and configured with Rails
- [ ] FactoryBot set up for test data generation
- [ ] Capybara configured for system testing
- [ ] SimpleCov configured for coverage reporting
- [ ] Database Cleaner configured for test isolation
- [ ] Example test files created for models, controllers, and features

## Technical Notes
- Configure RSpec with Rails-specific matchers
- Use FactoryBot instead of fixtures for maintainable test data
- Set up headless Chrome for system tests
- Configure test database separate from development
```

### 2. Set up Code Quality Tools
```markdown
## Summary
Configure RuboCop, Brakeman, and Rails Best Practices for code quality

## Acceptance Criteria
- [ ] RuboCop configured with Rails and community style guides
- [ ] Brakeman configured for security analysis
- [ ] Rails Best Practices gem installed
- [ ] Pre-commit hooks configured
- [ ] CI pipeline includes code quality checks
- [ ] Code quality baseline established

## Technical Notes
- Use rubocop-rails and rubocop-rspec extensions
- Configure custom cops for project-specific rules
- Set up Brakeman to run on CI and ignore false positives
```

### 3. Set up Background Jobs
```markdown
## Summary
Configure Sidekiq for background job processing with monitoring

## Acceptance Criteria
- [ ] Sidekiq installed and configured
- [ ] Redis configured for job storage
- [ ] Example background job created
- [ ] Sidekiq web UI configured
- [ ] Job retry and failure handling configured
- [ ] Development and production job configurations

## Technical Notes
- Use Sidekiq for better performance than DelayedJob
- Configure different queues for different job types
- Set up proper error handling and monitoring
```

## Common Rails Patterns

### Model Example
```ruby
# app/models/user.rb
class User < ApplicationRecord
  has_secure_password
  
  has_many :posts, dependent: :destroy
  has_one_attached :avatar
  
  validates :email, presence: true, uniqueness: true
  validates :name, presence: true, length: { minimum: 2 }
  
  scope :active, -> { where(active: true) }
  scope :recent, -> { order(created_at: :desc) }
  
  before_save :normalize_email
  
  private
  
  def normalize_email
    self.email = email.downcase.strip
  end
end
```

### Controller Example
```ruby
# app/controllers/users_controller.rb
class UsersController < ApplicationController
  before_action :authenticate_user!
  before_action :set_user, only: [:show, :edit, :update, :destroy]
  
  def index
    @users = User.active.recent.page(params[:page])
  end
  
  def show
  end
  
  def create
    @user = User.new(user_params)
    
    if @user.save
      redirect_to @user, notice: 'User was successfully created.'
    else
      render :new, status: :unprocessable_entity
    end
  end
  
  private
  
  def set_user
    @user = User.find(params[:id])
  end
  
  def user_params
    params.require(:user).permit(:name, :email, :password, :password_confirmation)
  end
end
```

### Service Object Example
```ruby
# app/services/user_registration_service.rb
class UserRegistrationService
  def initialize(user_params)
    @user_params = user_params
  end
  
  def call
    ActiveRecord::Base.transaction do
      create_user
      send_welcome_email
      create_default_preferences
      
      Result.new(success: true, user: @user)
    end
  rescue ActiveRecord::RecordInvalid => e
    Result.new(success: false, errors: e.record.errors)
  end
  
  private
  
  attr_reader :user_params
  
  def create_user
    @user = User.create!(user_params)
  end
  
  def send_welcome_email
    UserMailer.welcome(@user).deliver_later
  end
  
  def create_default_preferences
    @user.create_preferences!(theme: 'light', notifications: true)
  end
  
  Result = Struct.new(:success, :user, :errors, keyword_init: true) do
    def success?
      success
    end
  end
end
```

### RSpec Test Example
```ruby
# spec/models/user_spec.rb
require 'rails_helper'

RSpec.describe User, type: :model do
  describe 'validations' do
    it { should validate_presence_of(:email) }
    it { should validate_uniqueness_of(:email) }
    it { should validate_presence_of(:name) }
    it { should validate_length_of(:name).is_at_least(2) }
  end
  
  describe 'associations' do
    it { should have_many(:posts).dependent(:destroy) }
    it { should have_one_attached(:avatar) }
  end
  
  describe 'scopes' do
    let!(:active_user) { create(:user, active: true) }
    let!(:inactive_user) { create(:user, active: false) }
    
    describe '.active' do
      it 'returns only active users' do
        expect(User.active).to include(active_user)
        expect(User.active).not_to include(inactive_user)
      end
    end
  end
  
  describe '#normalize_email' do
    it 'normalizes email before saving' do
      user = build(:user, email: '  TEST@EXAMPLE.COM  ')
      user.save!
      expect(user.email).to eq('test@example.com')
    end
  end
end

# spec/factories/users.rb
FactoryBot.define do
  factory :user do
    name { Faker::Name.name }
    email { Faker::Internet.email }
    password { 'password123' }
    password_confirmation { 'password123' }
    active { true }
    
    trait :inactive do
      active { false }
    end
    
    trait :with_posts do
      after(:create) do |user|
        create_list(:post, 3, user: user)
      end
    end
  end
end
```

## Recommended Gemfile

```ruby
# Gemfile
source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby '3.2.0'

gem 'rails', '~> 7.1.0'
gem 'pg', '~> 1.1'
gem 'puma', '~> 6.0'
gem 'sass-rails', '>= 6'
gem 'webpacker', '~> 5.0'
gem 'turbo-rails'
gem 'stimulus-rails'
gem 'jbuilder', '~> 2.7'
gem 'bootsnap', '>= 1.4.4', require: false
gem 'image_processing', '~> 1.2'

# Authentication & Authorization
gem 'devise'
gem 'pundit'

# Background Jobs
gem 'sidekiq'
gem 'redis', '~> 5.0'

# UI & Assets
gem 'tailwindcss-rails'
gem 'stimulus-rails'

group :development, :test do
  gem 'rspec-rails'
  gem 'factory_bot_rails'
  gem 'faker'
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
end

group :development do
  gem 'web-console', '>= 4.1.0'
  gem 'listen', '~> 3.3'
  gem 'spring'
  gem 'rubocop-rails', require: false
  gem 'rubocop-rspec', require: false
  gem 'brakeman', require: false
  gem 'rails_best_practices', require: false
end

group :test do
  gem 'capybara', '>= 3.26'
  gem 'selenium-webdriver'
  gem 'webdrivers'
  gem 'simplecov', require: false
  gem 'database_cleaner-active_record'
  gem 'shoulda-matchers'
end
```

## Rails Best Practices for CCWF

1. **Convention Over Configuration**: Follow Rails conventions for predictable code structure
2. **Fat Models, Skinny Controllers**: Keep business logic in models or service objects
3. **Service Objects**: Use service objects for complex business operations
4. **Background Jobs**: Use Sidekiq for time-consuming tasks
5. **Testing**: Write comprehensive tests with RSpec and system tests
6. **Security**: Use strong parameters, CSRF protection, and security headers
7. **Performance**: Use eager loading, database indexes, and caching appropriately
8. **Code Quality**: Maintain consistent style with RuboCop and regular code reviews
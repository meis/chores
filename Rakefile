require 'capybara/poltergeist'
require 'phantomjs'

task :packt_free_ebook do
  Capybara.current_driver = :poltergeist
  Capybara.register_driver :poltergeist do |app|
    options = {
      phantomjs: Phantomjs.path,
      phantomjs_options: ['--load-images=no', '--ignore-ssl-errors=yes'],
    }
    Capybara::Poltergeist::Driver.new(app, options)
  end

  browser = Capybara.current_session

  browser.visit 'https://www.packtpub.com/packt/offers/free-learning'
 
  browser.find('.login-popup', visible: false).trigger('click')
  browser.fill_in 'email', with: ENV['PACKT_EMAIL']
  browser.fill_in 'password', with: ENV['PACKT_PASSWORD']
  browser.click_on('Login')

  browser.click_on('Claim Your Free eBook')
end

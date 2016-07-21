require 'capybara/webkit'

task :packt_free_ebook do
  Capybara.current_driver = :webkit
  Capybara::Webkit.configure do |config|
    config.allow_unknown_urls
    config.skip_image_loading
  end

  browser = Capybara.current_session

  browser.visit 'https://www.packtpub.com/packt/offers/free-learning'

  browser.find('.login-popup').trigger('click')
  browser.fill_in 'email', with: ENV['PACKT_EMAIL']
  browser.fill_in 'password', with: ENV['PACKT_PASSWORD']
  browser.click_on('Login')
  browser.click_on('Claim Your Free eBook')
end

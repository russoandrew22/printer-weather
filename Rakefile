# This task can be run by CRON, or Heroku's Scheduler addon, to dispatch
# the weather data to the servers at 8am.

task :run do
  $LOAD_PATH.unshift "."
  require "job"
  require "net/http"
  require "uri"
  puts "Running weather jobs."
  Job.each do |j|
    puts "Processing job #{j.id}: #{j.print_url}"
    Net::HTTP.post_form(URI.parse(j.print_url), url: "http://weatherprint.herokuapp.com/weather/#{j.id}")
  end
end

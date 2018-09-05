# Background-Jobs-in-ROR

Background jobs are used for executing tasks in which we don't need instant response. E.g Encoding video, generating sitemap, generating product listing feeds, image thumbnail generation etc

Rails provides lot of gems for background job processing but i am sharing these 2 according to my experience on moderate and huge traffic websites

1- [Delayed_job](https://github.com/collectiveidea/delayed_job)
2- [Sidekiq](https://github.com/mperham/sidekiq)

## Delayed_job:
This is oldest gem that i initially used in some of the projects and it worked quite well. But there are following pros & cons in comparison to Sidekiq.

Pros:

1- No extra tool required, by default uses main project db.

2- Suitable for project with few jobs on daily basis.

Cons: 

1- By default use database as backend store and send lot of queries to main DB server in case of large no of jobs on daily basis.

2- No control panel for tracking jobs status and statistics

3- Don't take advantage of multi-threading.

 Some useful commands:

 RAILS_ENV=production script/delayed_job -n 2 start # n represent no of worker process you want to start to process jobs.

 RAILS_ENV=production script/delayed_job stop
 
## Sidekiq :

This is very good gem and i have used it in many projects. This gem has following pros & cons of gems in comparsion to delayed_job

Pros:

 1- By default use Redis as backend store and you can offload lot of queries from your main db server in case of large no of jobs on daily basis. Redis is very fast as compared to RDBMS.

 2- Good control panel for tracking job status, resubmit job, queue status and queue statistics etc. 

 3- Long list of third party add-on plugins to extend functionality according to needs.

 4- Good utilization of CPU by using multi-threading

 Cons: 

 1- Extra software(Redis) required.
 

Some interesting addons for getting more control on job execution flow:
 
1- [Sidekiq Priority](https://github.com/publitas/sidekiq-prioritized_queues)

2- [Sidekiq Limit Fetch](https://github.com/brainopia/sidekiq-limit_fetch)

3- [Sidekiq Throttler](https://github.com/gevans/sidekiq-throttler)


Some useful commands: 

RAILS_ENV=production bundle exec sidekiq -c 10 -q critical,8 -q default # this job create 10 threads

[Admin panel snapshot]: https://github.com/mperham/sidekiq/raw/master/examples/web-ui.png

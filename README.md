# Background-Jobs-in-ROR

Background jobs are used for executing tasks in which we don't need instant response. E.g Encoding video, generating sitemap, generating product listing feeds, image thumbnail generation etc

Rails provides lot of gems for background job processing but i am sharing these 2 according to my experience on moderate and huge traffic websites

1) [Delayed_job](https://github.com/collectiveidea/delayed_job)
2) [Sidekiq](https://github.com/mperham/sidekiq)

# Delayed_job:
This is oldest gem that i initially used in some of the projects and it worked quite well. But there are following pros & cons in comparison to Sidekiq.

Pros :

1- No extra tool required, by default uses main project db.

2- Suitable for project with few jobs on daily basis.

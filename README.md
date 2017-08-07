# postgresql
community postgresql release

Edit `configuration.yml` and change the region to match the closest geographic AWS [region](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-available-regions). Run via the following:

     AWS_PROFILE=datanexus ./provision-postgresql

Connect to the Linux instance (the code will modify your ~/.ssh/config):
     
     ssh dn_postgresql
     
Connect to the postgresql database:

     sudo -u postgres -i psql
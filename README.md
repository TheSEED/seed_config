SEED configuration module

This module is responsible for creating the FIG_Config.pm that is used throughout the SEED codebase.

A standard SEED deployment has historically had a single directory hierarchy within which
both the code and data reside.

With the release engineering here we are splitting the two. The code deploys into a standard
PATRIC-style deployment. The data, managed by the code in the seed_db module, is in an independent
location and in fact may be referenced by multiple deployments if desired.


Notes on deployment flag

app_service/Makefile:	$(TPAGE) --define deployment_flag=1 $(TPAGE_DEPLOY_ARGS) $(TPAGE_ARGS) dancer_config.yml.tt > $(TARGET)/services/$(SERVICE)/config.yml

./app_service/dancer_config.yml.tt:[% ELSIF deployment_flag -%]


# bring Flask server up
run: deps
	dev_appserver.py . \
		--skip_sdk_update_check=yes \
		--host=0.0.0.0 \
		--port=8080 \
		--admin_host=0.0.0.0 \
		--admin_port=8081 \
		--api_host=0.0.0.0 \
		--api_port=8082


deps: requirements.txt
	pip install -r requirements.txt -t lib


# deploy to the configured APP and VERSION. Will force a migration first.
deploy: deps
	appcfg.py update . \
		--oauth2 \
		--oauth2_credential_file=/tmp/.deploy_credentials \
		--noauth_local_webserver \
		-A $(APP) \
		-V $(VERSION)


clean:
	find . -name "*.pyc" -exec rm -rf {} \;


# Makefile ettiquette
.PHONY: run deps deploy clean

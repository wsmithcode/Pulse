deploy:
	echo @"Deploying Pulse Application"
	docker compose --env-file .env -f docker-compose.yml up -d --build --force-recreate
	echo @"Pulse Application Deployed"
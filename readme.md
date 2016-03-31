Testing procedure


setup the environment and check out file
```
Connect to Office LAN

cd <our security test home>
git clone http://dsdp.pccw.com:9091/raymondng/fiware.security.test.git
export FIWARE_SEC_HOME=<your secirty testing home>/fiware.security.test

# or chand directory to that directory and run
# export FIWARE_SEC_HOME=$PWD
```

Add the current user to docker group
```
suod usermod -aG docker ${USER}
```

Start docker containers
```
cd ${FIWARE_SEC_HOME}/docker
docker-compose -f docker-compose-deps.yml up -d
```

If you get the following error, you need to run docker-compose up again. This error is normal when we start many docker in docker-compose.
```
ray@ubuntu:~/security.test.working/fiware.security.test/docker$ docker-compose up
Creating mariadb
Creating authzforce
Creating idm
ERROR: An HTTP request took too long to complete. Retry with --verbose to obtain debug information.
If you encounter this issue regularly because of slow network conditions, consider setting COMPOSE_HTTP_TIMEOUT to a higher value (current value: 60).
```

You may stop docker-compose by
```
cd ${FIWARE_SEC_HOME}/docker
docker-compose -f docker-compose-deps.yml down
```

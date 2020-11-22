# node-js_redis_ansible
Node JS with redis and HA deployment using ansible

Following are the objectives of the code.
Setup a machine using ansible for following:
- Host simple node js server to server hello world API
- API should server response using redis cache
- Cache should invalidate very 1 min
- Implement HA for Redis and Nodejs

## Getting Started

Get Machines from the cloud vendor. It can be from aws/gcp/digital-ocean

### Prerequisites


```
* ansible installed.
* for local testing docker and docker compose
```

## FileStructure
Following is the file structure for the project.

```
docker-swarm/                             #{ansible role file}
            -/README.md
            -/defaults/main.yml
            -/handlers/main.yml
            -/meta/main.yml
            -/tasks/main.yml
hosts                                     #{ansible inventory file}
nodeJsProject/                            #{Nodejs-redis project root directory}
            -/Dockerfile                  #{Dockerfile for building standalone nodejs project}
            -/docker-compose.yml          #{docker stack deployment file. Include image from hub.docker.com instead of build directive}
            -/index.js                    #{index file for node app}
            -/package-lock.json
            -/package.json                #{file with dependencies mentioned}
docker-swarm.yml                          #{ansible playbook for deploying swarm and the nodejs application.}
```

## Deployment

Following are the steps for deployment.

```
ansible-playbook -i hosts docker-swarm.yml
```

## Troubleshooting

Error may come due to default network adaptor not having value is eth1 or the default adaptor would have two ip addresses. For this chooes the adaptor with private subnet address. And the other machines can be accessed from it.

```
export device=<device-adaptor-name>
sed -i "s/eth0/${device}/g" docker-swarm.yml
```



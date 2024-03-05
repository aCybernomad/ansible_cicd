# Ansible playbook

### Hämta appens image från Docker Hub

```yml
- name: Pull Docker image
  shell: "docker pull bugzapper/iss-app-cicd:latest"
```

### Ladda ner och mounta en docker volume (postgresql)

```yml
- name: Run PostgreSQL Docker container
  shell: "docker run --rm -e POSTGRES_PASSWORD=pass -e POSTGRES_USER=awesome -e POSTGRES_DB=iss-db -p 5432:5432 -v pgdata:/var/lib/postgresql/data -d postgres"
```

### Kör igång appen mha Docker imagen

```yml
- name: Kör appens Docker Image som nyss laddades ner
  shell: "docker run -p 3000:3000 -e PG_HOST={{ ansible_default_ipv4.address }} -d bugzapper/iss-app-cicd:latest"
```

[![Build Status](https://cloud.drone.io/api/badges/klamouri/karim-docker-images/status.svg)](https://cloud.drone.io/klamouri/karim-docker-images)

This repository aim is to provide myself and coworkers ready to use shell environments with version pinned software
to perform our daily duties without sacrificing user-friendliness. The docker images all have ZSH and Oh-My-Zsh plugin 
as it is my main shell and framework on my laptop and I like to keep it consistent.
I tested the Oh-My-Zsh theme with Solarized Light.

Example to get access to Kafka CLI on your laptop:
```$zsh
docker run -it --rm karimlamouri/confluent-oss-4.1.4:latest
```

This would launch a docker container that have kafka-cli installed and an Oh-My-ZSH shell. Making it seamless if you use
Oh-My-ZSH on your laptop.
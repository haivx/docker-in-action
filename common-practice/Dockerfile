# 1. using COPY, not ADD
#   - ADD command does extra things, can make side effects. So should'n use it unless you know why you need it
# 2. Using CMD with node, not npm
#   - npm require another application to run(node is running as a sub process) 
#   - not literal as dockerfile
#   - npm doesnt work well as an init process or PID 1 process
# 3. Using WORKDIR not mkdir
#   - WORKDIR will create a directory if it's not there
#   - Unless you need chown: if you need specific permissions on a directory when it's created, just using mkdir

#4. Base image
#  - Stick to even numberer major releases, dont use :lastest tag because it lacks of stable
#  - Start with debian if youre migrating from old to new system
#      - all Official images on dockerhub default to Debian which mean you get the apt package manager out of the box, and you can run other command like Ubuntu 
#  - Move to alpine: 
#  - Dont use slim tag: smaller than alpine and lack of utilites
#
#5: Using Node user
#  - Official node images has a node user
#  - But its not used by default
# - assign node user after apt/apk npm i -g because these command are not available without root permissions
#  - assign node user after npm command because it can cause permissions isssues related with write access
#  - WORKDIR command need root permissions, so using chown after this command

FROM --platform=linux/amd64 node:14 As development

RUN mkdir -p /app

WORKDIR /app

COPY package.json ./

COPY . .

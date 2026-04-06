FROM nginx:1.29.7-alpine
RUN wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/conf.d/globalblacklist.conf -O /etc/nginx/conf.d/globalblacklist.conf &&\
    mkdir /etc/nginx/bots.d &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/bots.d/blockbots.conf -O /etc/nginx/bots.d/blockbots.conf &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/bots.d/ddos.conf -O /etc/nginx/bots.d/ddos.conf &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/bots.d/whitelist-ips.conf -O /etc/nginx/bots.d/whitelist-ips.conf &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/bots.d/whitelist-domains.conf -O /etc/nginx/bots.d/whitelist-domains.conf &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/bots.d/blacklist-user-agents.conf -O /etc/nginx/bots.d/blacklist-user-agents.conf &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/bots.d/custom-bad-referrers.conf -O /etc/nginx/bots.d/custom-bad-referrers.conf &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/bots.d/blacklist-ips.conf -O /etc/nginx/bots.d/blacklist-ips.conf &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/bots.d/bad-referrer-words.conf -O /etc/nginx/bots.d/bad-referrer-words.conf &&\
    wget https://raw.githubusercontent.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker/master/conf.d/botblocker-nginx-settings.conf -O /etc/nginx/conf.d/botblocker-nginx-settings.conf &&\
    printf "\n172.21.0.1        0;\n" >> /etc/nginx/bots.d/whitelist-ips.conf &&\
    printf "\n81.19.141.81      1;\n" >> /etc/nginx/bots.d/blacklist-ips.conf &&\
    printf "\n\"~*(?:\\\b)python\\-httpx(?:\\\b)\"	3;\n" >> /etc/nginx/bots.d/blacklist-user-agents.conf &&\
    printf "\n\"~*(?:\\\b)go\\-resty(?:\\\b)\"	3;\n" >> /etc/nginx/bots.d/blacklist-user-agents.conf &&\
    printf "\n\"~*(?:\\\b)go\\-http\\-client(?:\\\b)\"	3;\n" >> /etc/nginx/bots.d/blacklist-user-agents.conf &&\
    printf "\n\"~*(?:\\\b)Python\\-urllib(?:\\\b)\"	3;\n" >> /etc/nginx/bots.d/blacklist-user-agents.conf

RUN mkdir -p /var/lib/nginx/proxy_cache
COPY ./core/* /etc/nginx/
CMD ["nginx", "-g", "daemon off;"]

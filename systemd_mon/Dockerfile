FROM ruby:latest

RUN gem install systemd_mon
RUN gem install mail
RUN gem install slack-notifier
RUN gem install hipchat

ENV CONFIG '{"verbose":true}'

ENTRYPOINT ["/bin/bash", "-c"]

CMD ["systemd_mon <(ruby -ryaml -rjson -e 'puts YAML.dump(JSON.parse(ENV[\"CONFIG\"]))')"]

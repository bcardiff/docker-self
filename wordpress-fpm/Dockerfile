FROM wordpress:4.6-fpm

# Install sSMTP for mail support
RUN apt-get update \
  && apt-get install -y -q --no-install-recommends \
  ssmtp zlib1g-dev \
  && apt-get clean \
  && rm -r /var/lib/apt/lists/*

RUN mkdir -p /usr/local/etc/php/conf.d/ \
  && mkdir -p /etc/ssmtp/ \
  && ln -sf /config/php-mail.conf /usr/local/etc/php/conf.d/mail.ini \
  && ln -sf /config/uploads.ini /usr/local/etc/php/conf.d/uploads.ini \
  && ln -sf /config/ssmtp.conf /etc/ssmtp/ssmtp.conf \
  && ln -sf /config/revaliases /etc/ssmtp/revaliases

RUN docker-php-ext-install zip

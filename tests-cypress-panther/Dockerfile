# Start from the latest Debian image
FROM debian:12-slim

# Update the system and install necessary packages
RUN apt-get update
RUN apt-get install -y \
    curl \
    chromium chromium-driver \
    sqlite3 \
    wget \
    gnupg2 \
    ca-certificates \
    lsb-release \
    apt-transport-https \
    unzip

# Install Node.js and npm
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
RUN apt-get install -y nodejs

# Install Yarn
RUN npm install --global yarn

# Install PHP 8.3 and extensions
RUN wget https://packages.sury.org/php/apt.gpg
RUN apt-key add apt.gpg
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/php.list
RUN apt-get update
RUN apt-get install -y php8.3 php8.3-curl php8.3-gd php8.3-xml php8.3-zip php8.3-sqlite3 php8.3-intl php8.3-mbstring

# Install Xdebug
RUN apt-get install -y php8.3-xdebug

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install Symfony
RUN wget https://get.symfony.com/cli/installer -O - | bash
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

# Install Cypress and Panther requirements
RUN apt-get install -y libgtk2.0-0 libgtk-3-0 libgbm-dev libnotify-dev libnss3 libxss1 libasound2 libxtst6 xauth xvfb

# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

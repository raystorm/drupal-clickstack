# Symfony

## Implementations

If you'd like to test this stack, have a look at the ClickStarts that implement 
it:

#### **TODO:** create a Click-Start

## About

This stack installs and serves your Symfony installations, easily.

To start with this stack, follow those steps:  

- Create a Symfony Application as normal  
  (download, composer, etc)  
- prepare the application to be deployed

        php ../composer.phar install --no-dev --optimize-autoloader

  other common deployment steps are handled by this clickstack at deployment time on the server.

- Zip the contents of your Symfony Application Directory  
  Typically: "framework-standard-edition"
  (e.g., `zip -r MY_PACKAGE.zip .`)
- Update Monolog configuration (details below)
- Deploy to Cloudbees:

        bees app:deploy -a MY_APP -t symfony-clickstack \ 
        -RPLUGIN.SRC.symfony-clickstack=https://s3.amazonaws.com/clickstacks/raystorm/symfony-plugin.zip \ 
        MY_PACKAGE.zip

Then the Stack will install everything for you, and you should land on the Symfony main page, ready to go!


## Configuration Changes:

### MonoLog  

Update monolog to log information to Stdout and/or Stderr

   monolog:
     handlers:
       stdout:
         type:  stream
         path:  "php://stdout"
         level: debug
       stderr: 
         type:  stream
         path:  "php://stderr"
         level: warning        


## More info

###[PHP ClickStack](https://github.com/cloudbees-community/php-clickstack)

## License

This work is distributed under the Apache license, found in the LICENSE file.

# Behat 3.5 + MinkExtension 2.3
---
Example of how to run Behat on Windows
##Composer.json
```json
{
	
    "require-dev": {
        "behat/behat": "^3.5",
        "behat/mink": "^1.7",
        "behat/mink-extension": "^2.3",
        "behat/mink-goutte-driver": "^1.2",
        "behat/mink-selenium2-driver": "^1.3"
    }
}
```

##How run SeleniumServer
Selenion path: 
>behat/lib
```bash
java -jar selenium-server-standalone-3.141.59.jar
```

##behat.yml
```yaml
default:
    extensions:
        Behat\MinkExtension:
            default_session: selenium2
            goutte: ~
            selenium2:
                # chrome
                wd_host: "http://127.0.0.1:4444/wd/hub"
                # chrome
                capabilities: { "browserName": "chrome", "browser": "chrome", "version":  "70", 'chrome': {'switches':['--no-sandbox']}}
            base_url: 'http://google.com/'
            # chrome
            browser_name: chrome
            files_path: 'files'
    suites:
        default:
            contexts:
                - FeatureContext
                - Behat\MinkExtension\Context\MinkContext
```

##How run *.feature
```bash
php behat feature\test
```
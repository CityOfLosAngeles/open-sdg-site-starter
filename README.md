# Open SDG - Site starter ![Build and Deploy Development Static Site](https://github.com/CityOfLosAngeles/open-sdg-site-starter/workflows/Build%20and%20Deploy%20Development%20Static%20Site/badge.svg) ![Build and Deploy Production Static Site](https://github.com/CityOfLosAngeles/open-sdg-site-starter/workflows/Build%20and%20Deploy%20Production%20Static%20Site/badge.svg)


This is a starter repository to help in implementing the [Open SDG](https://github.com/open-sdg/open-sdg) platform. [See here for documentation](https://open-sdg.readthedocs.io).

### Testing w/ Jekyll Locally

#### Preparing the SDG Data Site

You will need to build the SDG Data site first locally in order to proceed with building and testing the SDG Site Starter first.

1.) Refer to the commands in https://github.com/CityOfLosAngeles/open-sdg-data-starter to setup your local environment.

2.) Proceed to navigate to the `_site` in the terminal of VS Code while in the container after building the data site locally and run `python3 -m http.server 9000`.

3.) The data site is now accessible via `localhost:9000`.

4.) In a separate VS Code window have this project opened and navigate to the `_config.yml` file and change `remote_data_prefix:` set to `"http://localhost:9000"`. Remember to revert this change before committing.

5.) Proceed with the steps below after running `bundle check --path=vendor/bundle || bundle install --path=vendor/bundle` to install the necessary dependencies.

**Test what development will look like by running the following command:**

`bundle exec jekyll serve --config _config.yml`

**Test what production will look like by running the following command:**

`bundle exec jekyll serve --config _config.yml,_config_prod.yml`

For each command listed above, you will be able to access the site locally by visiting `http://127.0.0.1:4000/`. Please be aware that not everything may load due to CORS. You may verify this with ChromeDevTools for example.

**To build the development site locally and have `_site` directory updated and available:**

`bundle exec jekyll build --config _config.yml`. Run `bash scripts/test/html_proofer_staging.sh` to perform html validation.

**To build the development site locally and have `_site` directory updated and available:**

`bundle exec jekyll build --config _config.yml,_config_prod.yml`. Note you may need to change the `remote_data_prefix:` in `_config_prod.yml` appropraitely as you see fit. Run `bash scripts/test/html_proofer_prod.sh` to perform html validation.

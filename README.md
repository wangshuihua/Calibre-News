# Calibre News Delivery

Leverages GitHub Actions to automate the delivery of Calibre News.

## Shortcut

 __[Workflow](../../actions/workflows/calibre-news.yml)__ | __[Actions](../../actions)__ | __[Environments](../../settings/environments)__ | [Enable/Disable](../../settings/actions) | [Destroy](../../settings#danger-zone)

## Setup

1) Create a project in your repositories using this template.
2) Navigate to [ __[Settings](../../settings)__ > __[Environments](../../settings/environments)__ ] in the project.
3) Click "__New environment__" to create a new one called `calibre-news`.
4) Add the required "__environment secrets__" to it as follows.

|Name|Required|Description|Example|
|---|---|---|---|
|FROM|Yes|Your email address|xxx@gmail.com|
|TO|Yes|Destination email address|xxx@kindle.com|
|ENCRYPT|Yes|SMTP encryption method|SSL|
|SECRET|Yes|SMTP password|xxxxxxxxxx|
|SMTP|Yes|SMTP server|smtp.gmail.com|
|PORT|Yes|SMTP port|465|
|FORMAT|No|The ebook format|epub|

5) Navigate to "[Actions](../../actions)" and click [ __Calibre News Delivery__ > __Run workflow__ ] to test.

## Schedule

The default delivery is scheduled to occur daily at midnight (00:00) UTC. You can change it according to your preference. The cron expression `- cron: '0 0 * * *'` can be found in the workflow file located at:

```
/.github/workflows/calibre-news.yml
```

Please refer to the "__[schedule](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#schedule)__" documentation to specify an appropriate time. For example, if you are in a timezone that is UTC+8 and want the delivery to start at 6:00 AM every day, you can set the cron expression as `0 22 * * *`, calculated using the formula `UTC Time = Local Time − Offset`.

Additionally, you can manually trigger the delivery on the "[Actions](../../actions)" page of your project.

## Recipe

For the built-in recipes, you need to add their names to the plain text file __[recipe_list.txt](recipe_list.txt)__, one name per line. For manually written recipes, simply place them in the root of the project.

## Notice

This project does not accept any PRs for adding recipes. Please do something interesting on your own.

## Links

* [API documentation for recipes](https://manual.calibre-ebook.com/news_recipe.html)
* [Calibre recipe repository](https://github.com/kovidgoyal/calibre/tree/master/recipes)
* [Adding your favorite news website](https://manual.calibre-ebook.com/news.html)

## License

[GNU General Public License v3.0](LICENSE)

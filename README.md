## Background story

Understanding the Craft CMS eco system is important to fortrabbit. The "marketing team" requires a tool to analyze data about available Craft plugins. Your job is to deliver data for the marketing team.

## Task

- Create a stand-alone PHP CLI that provides a list of all composer packages of type `craft-plugin`.
- Output the data as a table or to a `json`file, see definition below.
- Create a GitHub repo that contains the code.
- Write a `README.md` that explains the tool.

## Key features

- Query the `packagist.org` API to retrieve the data ([follow the best practices when using the API](https://packagist.org/apidoc)).
- When working with the data set, performance is more important than real time data.
- Skip abandoned packages.
- Consider this tool NOT as a one-off-script, treat it as a piece of software that is maintained in the long run.

## Command options

```jsx
--limit (defaults to 50)
--orderBy (field, allowed values: downloads, favers, dependents, updated (defaults to downloads))
--order (ASC or DESC (defaults to DESC))
--output (path to the json file (if not set, table output to stdout is expected))
```

## Hints / Coding suggestions

- The entire list of packages contains ~1.600 items
- Make use of PHP 8 language constructs if they make sense to you
- Make use of existing packages if they make sense to you
- There is probably more than one API call are required to retrieve the data
- There is no knowledge about Craft CMS required. In theory, analyzing other [package types](https://getcomposer.org/doc/04-schema.md#type) can make sense in the future.
- Defining the name of the tool is up to you
- Demonstrate best practices (e.g. OOP, tests, docs), but be pragmatic.

### Work with collections of objects described below

```php
class CraftPluginPackage implements \JsonSerializable
{
  public string $name;
  public string $description;
  public string $handle; // versions[0].extra.handle attribute
  public string $repository;
  public ?string $testLibrary;
  public string $version; // most recent branch
  public int $downloads; // downloads.monthly
  public int $dependents;
  public int $favers;
  public DateTime $updated;
}
```

See the schema to understand the `handle` attribute: [https://craftcms.com/docs/3.x/extend/plugin-guide.html#composer-json](https://craftcms.com/docs/3.x/extend/plugin-guide.html#composer-json)

## **Don't do**

- Don't register the package on packagist
- Don't create a `.phar`

## Timing

- Please complete within 7 days
- The task should not require more than 10 hours of focused work (take a break)
- Please also let us know

## Questions and feedback

- [Create an issues](https://github.com/fortrabbit/interview-task-php/issues) with this repo.
- Ask early if things are not clear
- Tell us if you are stuck, it's not a shame to ask for help
- Let us know when you are done
- We will review the code and have a chat about it - don't be afraid, it's just tech-talk

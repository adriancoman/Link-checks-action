# Link checks action

GitHub action that checks if the links provided in a file are valid (they return a 200 response code) or if they return an error.

We found that when adding new links some bad copy paste could happen that's easy to miss. As well, it can happen during a refactor that involces a lot of renaming. 
This action is a safety net to make sure our URLs not get shipped broken.

## Hot to use
In order to run the action, add it to your yml file
```yml
- name: Run URL check script
  uses: adriancoman/link_checks@1.0.0
  with:
    file-to-check: "{path_to_your_file}"
```

## Use cases
For our mobile app, we usually hold all of our T&C or external links in a file with constant values, ex:
```kotlin
object UrlConstants {
    const val TERMS = "https://www.my_awesome_website.com/terms.html"
    const val PRIVACY = "https://www.my_awesome_website.com/privacy.html"
}
```
So I created this action to notify us if a URL is broken.

## Contribution
There are a lot of improvements that can be added, from the top of my head:
- Check only modified files
- Accept a list of params, instead of a single file
- Change the http response code to be valid in the intervel [200..300)

But for now, it's a simple scrip that just works and it does it's job.

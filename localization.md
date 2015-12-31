# Localization (i18n)

The main language is `en_US`. All derived translations should be taken from this branch.

Supported languages so far are:

    * English [en_US]
    * Spanish [es_ES]

Possible future languages to include:

    * Italian [it_IT]
    * Portuguese [pt_BR]
    * Catalan [ca_ES]

# Directories

    * Translation key files are located in `resources/lang`
    * Email templates are located in `resources/views/emails` which are as well localized

# Translation Keys Schema

There is currently no proper *translation key schema* set.

So far, the key naming intends to achieve the following goals:

    * **Consistency:** Minimize the possibility of using different words for the same meaning, or creating many different keys that end up having the same translation (like common words).
    * **Reusability:** Minimize the overall translation files size and translate as less as possible, and preserve flexibility.
    * **Readability:** Translators should be able to easily identify the purpose of the key even under lack of the translation value.
    * **Organization:** Developer should easily remember/guess the full key path (or at least the base path) and minimize checking the transalation files each time.

You may find [further information in StackOverflow](http://stackoverflow.com/questions/31785471/which-are-the-suggested-key-naming-strategies-for-trans-in-laravel)

# Updating texts

Simply go to the translation key files or email template and update wordings.

# Adding keys

Follow [Laravel localization](https://laravel.com/docs/5.1/localization) facilities.

For automatically adding the translation key files, timegrid uses [potsky/laravel-localization-helpers](https://github.com/potsky/laravel-localization-helpers/).

You can do this by running

    php artisan localization:missing

Afterwards, edit each modified file to put the proper translation wording.

> *NOTE:* This tool will break PSR-2 standard for translation files. However, this [could possibly be fixed in the future](https://github.com/potsky/laravel-localization-helpers/issues/15).

# Adding a new language locale

## Copy from English and Edit method

1. Make sure to get the latest `en_US` translation tree of the project.
1. Copy the tree renaming it to the desired new locale.
1. Edit all keys to update the translations.

## From Scratch Method

1. Create the desired new locale driectory in the two resources locations: `lang` and `emails`.
1. Run the *laravel-localization-helpers* to generate the files.
1. Edit all keys to update the translations.

> This method might omit some dynamically generated keys.

# ZenstruckFormBundle

Provides Twitter Bootstrap form theme, useful FormType Extensions and javascript helpers

## Installation

1. Add to your `composer.json`:

    ```json
    {
        "require": {
            "zenstruck/form-bundle": "*"
        }
    }
    ```

2. Register the bundle with Symfony2:

    ```php
    // app/AppKernel.php

    public function registerBundles()
    {
        $bundles = array(
            // ...
            new Zenstruck\Bundle\FormBundle\ZenstruckFormBundle(),
        );
        // ...
    }
    ```

## Twitter Bootstrap form layout

To use, do one of the following:

- Add for a single template:

    ```jinja
    {% form_theme form 'ZenstruckFormBundle:Twitter:form_bootstrap_layout.html.twig' %}
    ```

- Add globally in your `config.yml`:

    ```yaml
    twig:
        form:
            resources:
                - 'ZenstruckFormBundle:Twitter:form_bootstrap_layout.html.twig'
    ```

## FormType Extensions

### HelpType

Allow you to add help messages to your form fields.

1. Enable in your `config.yml` (disabled by default):

    ```yaml
    zenstruck_form:
        form_types:
            help: true
    ```

2. Add help option to your form fields

    ```php
    use Symfony\Component\Form\AbstractType;
    use Symfony\Component\Form\FormBuilderInterface;

    class MyFormType extends AbstractType
    {
        public function buildForm(FormBuilderInterface $builder, array $options)
        {
            $builder
                ->add('name', 'text', array(
                    'help' => 'Your full name'
                ))
            ;
        }

        // ...
    }
    ```

## Javascript helpers

This bundle comes with a set of useful javascript helpers.  To enable, add the following javascipt file (or add to your
assetic javascripts):

```html+jinja
<script type="text/javascript" src="{{ asset('bundles/zenstruckform/js/helper.js') }}"></script>
```

### PostLinkHelper

Allows a standard `<a>` tag to become a method="POST" link.  Add the class `method-post` or `method-delete` to an `<a>`
tag for it's href value to become a POST link. Use the `method-delete` class to generate a confirmation dialog.

Enable with `ZenstruckFormHelper.initPostLinkHelper()`

### FormCollectionHelper

Adds Symfony2 form collection add and delete button functionality.  See the
[Symfony2 docs](http://symfony.com/doc/current/cookbook/form/form_collections.html).  This works out of the box when
using the `form_bootstrap_layout.html.twig` form layout provided by this bundle.

Enable with `ZenstruckFormHelper.initPostLinkHelper()`

## Full default config

```yaml
zenstruck_form:
    form_types:
        help: false
```
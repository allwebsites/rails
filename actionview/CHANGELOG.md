*   Allow custom `:host` option to be passed to `asset_url` helper that
    overwrites `config.action_controller.asset_host` for particular asset.

    *Hubert Łępicki*

*   Deprecate `AbstractController::Base.parent_prefixes`.
    Override `AbstractController::Base.local_prefixes` when you want to change
    where to find views.

    *Nick Sutterer*

*   Take label values into account when doing I18n lookups for model attributes.

    The following:

        # form.html.erb
        <%= form_for @post do |f| %>
          <%= f.label :type, value: "long" %>
        <% end %>

        # en.yml
        en:
          activerecord:
            attributes:
              post/long: "Long-form Post"

    Used to simply return "long", but now it will return "Long-form
    Post".

    *Joshua Cody*

*   Change `asset_path` to use File.join to create proper paths:

    Before:

        https://some.host.com//assets/some.js

    After:

        https://some.host.com/assets/some.js

    *Peter Schröder*

*   Change `favicon_link_tag` default mimetype from `image/vnd.microsoft.icon` to
    `image/x-icon`.

    Before:

        #=> favicon_link_tag 'myicon.ico'
        <link href="/assets/myicon.ico" rel="shortcut icon" type="image/vnd.microsoft.icon" />

    After:

        #=> favicon_link_tag 'myicon.ico'
        <link href="/assets/myicon.ico" rel="shortcut icon" type="image/x-icon" />

    *Geoffroy Lorieux*

*   Remove wrapping div with inline styles for hidden form fields.

    We are dropping HTML 4.01 and XHTML strict compliance since input tags directly
    inside a form are valid HTML5, and the absense of inline styles help in validating
    for Content Security Policy.

    *Joost Baaij*

*   `collection_check_boxes` respects `:index` option for the hidden filed name.

    Fixes #14147.

    *Vasiliy Ermolovich*

*   `date_select` helper with option `with_css_classes: true` does not overwrite other classes.

    *Izumi Wong-Horiuchi*

*   `number_to_percentage` does not crash with `Float::NAN` or `Float::INFINITY`
    as input.

    Fixes #14405.

    *Yves Senn*

*   Add `include_hidden` option to `collection_check_boxes` helper.

    *Vasiliy Ermolovich*

*   Fixed a problem where the default options for the `button_tag` helper is not
    applied correctly.

    Fixes #14254.

    *Sergey Prikhodko*

*   Take variants into account when calculating template digests in ActionView::Digestor.

    The arguments to ActionView::Digestor#digest are now being passed as a hash
    to support variants and allow more flexibility in the future. The support for
    regular (required) arguments is deprecated and will be removed in Rails 5.0 or later.

    *Piotr Chmolowski, Łukasz Strzałkowski*

Please check [4-1-stable](https://github.com/rails/rails/blob/4-1-stable/actionview/CHANGELOG.md) for previous changes.

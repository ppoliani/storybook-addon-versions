# storybook-addon-versions

This addon allows you to navigate different versions of your components, if you have a setup that produces a different static Storybook build for each of your versions. As such, if you build a static Storybook and host it in, say, the following directory structure:
```
- static-storybook
|-- 0.2.4
|-- 0.2.5
|-- 0.2.6
|-- 0.3.0
```

the addon will allow you to navigate the various versions as follows:

[[https://github.com/buildit/storybook-addon-versions/blob/master/docs/versions-demo.gif]]

## Configuration

This addon attempts to get a list of available style guide versions from the root of your host. If they are found it will show a dropdown which then lets you navigate to the various versions, as such allowing users to see how a component may have changed over different versions.

The versions are expected to be in a file `storybook-config.json` at the root of your host. You can also mock this in local dev by adding a `storybook-config.json` in your local `.storybook/` folder. Here's some sample content:

```
{
  "storybook": {
    "versions": [
      "0.2.4",
      "0.2.5",
      "0.2.6",
      "0.3.0"
    ],
    "regex": "\/([^\/]+?)\/?$"
  }
}
```

The `versions` field is just an array of the different available versions. The `regex` field is for a regular expression that will extract the version number for your URL. This is dependant on the way you store the static storybook builds. The example above will work for the format `http://localhost:port/<version>/` so for example, version `0.1.2` would be expected to be found like this `http://mystorybook/0.1.2/`.

The config format is the same as for [blabbr](https://github.com/buildit/storybook-addon-blabbr).


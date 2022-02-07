---
title: 'July 2021'
description: .
tree_item_index: 952
review:
  comment: ''
  date: '2021-07-13'
  status: ok
toc: true
---

{{! multiexcerpt name='studio-updates-2021-07'}}
### Studio Designer Accessibility Improvements

If you are using LTS 2021, [Nuxeo Web UI version 3.0.3](https://connect.nuxeo.com/nuxeo/site/marketplace/package/nuxeo-web-ui?version=3.0.3) brings new accessibility improvements targeted at better handling keyboard navigation and screen reader compatibility. If you are using LTS 2019 or older, you can skip this changelog.

As a developer, most of these changes are transparent for you and will be automatically applied with the update.

More specifically, anything that you configured besides layouts automatically receives our latest accessibility updates as soon as you install Web UI 3.0.3. No need for an update on your side. Existing layouts need to be updated to be more accessible. New ones created starting from June 22, 2021 will benefit from the latest accessibility updates.

Below is a more detailed breakdown of the changes.

#### Automatically Applied by Installing Web UI 3.0.3

- Tabs and drawer can be navigated using the keyboard ([WEBUI-191](https://jira.nuxeo.com/browse/WEBUI-191) and [WEBUI-192](https://jira.nuxeo.com/browse/WEBUI-192)).
- Tabs expose a role for improved accessibility ([WEBUI-317](https://jira.nuxeo.com/browse/WEBUI-317)).
- Buttons and drawer menu items expose a clear label when using voiceover ([WEBUI-200](https://jira.nuxeo.com/browse/WEBUI-200)). The label used by the voiceover tool will be the same as the one exposed to the users when hovering over it and shown in the tooltip.
- When listing documents in a list view or a grid view, images will have an alternative text. This is also true when viewing a single document containing an image or a video ([WEBUI-204](https://jira.nuxeo.com/browse/WEBUI-204)).

#### Requires a Manual Update to Your Existing Configuration in Nuxeo Studio

- Properties exposed in newly generated layouts or added to existing layouts are compatible with voiceover ([NXS-6346](https://jira.nuxeo.com/browse/NXS-6346)).

##### How Do I Update My Existing Configuration?

If your layout was created before June 22, 2021 you will need to update it manually to make it more accessible.

- Open an existing layout
- Use the “switch to code” option

- For every property in your layout, you’ll notice that the code looks as follows:

```
<div role="widget">
     <label>Files</label>
     <nuxeo-dropzone value="{{document.properties.files:files}}" multiple="true" name="files"></nuxeo-dropzone>
</div>
```

To benefit from a better accessibility, you need to add an identifier to the properties as follows:

```
<div role="widget">
     <label id="anIdOfYourChoosing">Files</label>
     <nuxeo-dropzone value="{{document.properties.files:files}}" multiple="true" aria-labelledby="anIdOfYourChoosing" name="files"></nuxeo-dropzone>
</div>
```

Make sure that every id remains unique in a given layout, and that the id expressed in the label matches the `aria-labelledby` property. Voiceover tools will use the `aria-labelledby` attribute to find the label with the corresponding id. The id itself doesn’t matter, it is only used to do the matching.

{{! /multiexcerpt}}
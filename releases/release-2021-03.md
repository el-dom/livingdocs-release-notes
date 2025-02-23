**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Newsletter](#newsletter)
- [Webinar](#webinar)
- [Patches](#repositories)
- [Highlights](#highlights)
- [Breaking Changes](#breaking-changes-fire)
- [Deprecations](#deprecations)
- [APIs](#apis-gift)
- [Internal Changes](#internal-changes)
- [Other Changes](#other-changes)

# Newsletter

* Subscribe here: https://confirmsubscription.com/h/j/61B064416E79453D


# Webinar

#### Features

* Recording: **TODO**
* Documentation: [here](https://docs.google.com/document/d/1gSbHm6nRBT0O8i9Z2UPvQ_PSLS_ZtGiy_qi8erTIMls)

#### Developers

* Recording: **TODO**
* Slides: **TODO**

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2021-03`
`@livingdocs/editor` | `release-2021-03`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2021-03",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2021-03

### Livingdocs Server Patches
- [v124.5.28](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v124.5.28): chore(openid): Move getOrCreateProject to support file
- [v124.5.27](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v124.5.27): chore(ww-assets): add tests for search
- [v124.5.26](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v124.5.26): chore: correctly pass trx to authIdentityModel.deleteIdentity




## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2021-03",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2021-03

### Livingdocs Editor Patches
- [v63.8.35](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.35): fix(multiselect): only allow to transform available components in a content-type
- [v63.8.34](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.34): fix(viewport-viewport-units-buggyfill): improve regex to match only vh units
- [v63.8.33](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.33): fix(link tool): allow to link to URLs matching the delivery path pattern but the extracted ID points to inexisting documents
- [v63.8.32](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.32): fix(link tool): make removing an existing link possible again
- [v63.8.31](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.31): fix(docked content): Visibility

- Fixed z visibility of project-setup's docked content (was in front of top right user menu on mobile)
- [v63.8.30](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.30): fix: add data-tour property for format-panel





# Highlights

## Media Library - Upload Center

When the user uploads images or videos, a new Upload Center is visible in the bottom right corner of the editor screen allowing the users to continue their work in the document while assets are uploaded in parallel in the background. If an error with any of the uploads happens it is shown and logged in the upload center.

<img width="377" alt="Screenshot 2021-03-08 at 21 26 16" src="https://user-images.githubusercontent.com/821875/110377665-f884e800-8054-11eb-9891-3f06aafc45ae.png">

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4145)


## Media Library - Media Sources :tada:

![image](https://user-images.githubusercontent.com/821875/107018818-35816480-67a1-11eb-945e-02f4838c5b61.png)

Allow to connect/integrate external asset services (e.g. Unsplash, Shutterstock, Pixabay, ...) as a Media Source in the Livingdocs Media Library. Working with a Media Source in Livingdocs feels the same as working with other assets of the Media Library.
The examples from the Livingdocs core all include free open source platforms, but of course one could also use media sources to integrate external DAM systems that might already be present in a publishers system landscape and by that consolidate the asset workflow for the journalists into Livingdocs.

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3266)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4106)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/357)


## Media Library - Index/Filter :tada:

The media library dashboard has now the same search and filter capabilites as the documents dashboard.
Define which media library metadata are indexed and define dashboard filter for all metadata.

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3389)
  * [Documentation plugin](https://docs.livingdocs.io/reference-docs/server-config/config#setting-up-the-media-library-elastic-search-mapping)
  * [Documentation mediaTypes](https://docs.livingdocs.io/reference-docs/project-config/media_types)
  * [Documentation baseFilters](https://docs.livingdocs.io/reference/base_filter#example-5-filter-by-metadata-with-datatype-keyword-for-mediaindex)
  * [Documentation custom Display Filter](https://docs.livingdocs.io/guides/register_custom_dashboard_filters_#register-custom-vue-component-filter)


## Media Library - Videos :tada:

![image](https://user-images.githubusercontent.com/4352425/98831646-2312bb80-243c-11eb-9211-5ea665b7e22c.png)

With this release we extend the [videos integration in the Media Library](https://docs.livingdocs.io/guides/media_library#videos) with new features:

- Define a poster image for videos
- Add configuration for video storage
- Several performance improvements


#### Shortcomings

Even when you are able to use videos in production, there are some shortcomings we want to share with you:

- There is no video service available (comparable with image services for images), the consequences are
  - The video tag uses the public url of the storage
  - Your video storage has to be public (or you don't see videos in the editor)
  - You have to render the document JSON with the video content on your own, otherwise the storage URL must be public in your delivery

Please get in touch if you want to integrate a transcoding pipeline or a video service.

References:
  * [Add Storage Config for Video](https://github.com/livingdocsIO/livingdocs-server/pull/3296)
  * [Video Storage Config Documentation](https://github.com/livingdocsIO/livingdocs/pull/350)
  * [Video Poster Image](https://github.com/livingdocsIO/livingdocs-editor/pull/4187)



## Named Crops :tada:

The Named Crops feature supports multiple crops per image in a document. This allows to preset crops on the master images in the Media Library and on demand overwrite those master crops on the placed image inside an article. Also, the API now provides several crops per image as defined in the named crops settings.

<img width="589" src="https://user-images.githubusercontent.com/821875/103688930-dc9c9180-4f92-11eb-894d-45ae105e72a4.png">


References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4051)
  * [Framework PR](https://github.com/livingdocsIO/livingdocs-framework/pull/511)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3261)
  * [Editor PR (Design Improvements)](https://github.com/livingdocsIO/livingdocs-editor/pull/4101)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/377)


## Notifications

<img width="285" alt="Screenshot 2021-03-03 at 17 19 37" src="https://user-images.githubusercontent.com/821875/109836673-af8ff680-7c44-11eb-8e21-628a4016ef87.png">

Notifications allow a user to subscribe to specific events of a document (e.g. a publish) and notifies this user via mail/slack when this event happens. Currently we support notification of task changes to the task requester and notification of document status changes to the document author.

References:
* [Documentation](https://github.com/livingdocsIO/livingdocs/pull/375)
* [Document Notifications](https://github.com/livingdocsIO/livingdocs-server/pull/3251)
* [Manage Document Subscriptions](https://github.com/livingdocsIO/livingdocs-server/pull/3344)
* [Manage Document Subscriptions UI](https://github.com/livingdocsIO/livingdocs-editor/pull/4013)


## Simplify Setup of Article Teasers

A simpler way to setup [Article Teasers](https://docs.livingdocs.io/guides/includes-embeds/article_teasers) is introduced. It is based on Includes and the possiblity to define the UI with a `paramsSchema` instead of writing code.

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/359)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3385)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4152)


## Multi Cluster Indexing :tada:

There are a bunch of new features for indexing
- Support multiple elasticsearch clusters during indexing
- Add config to enable/disable consumers (e.g. to disable consumers for a delivery instance)
- Custom indexes can target a specific elasticsearch cluster
- Improved error handling

References:
  * [Multi Cluster Indexing Preparation - I](https://github.com/livingdocsIO/livingdocs-server/pull/3299)
  * [Multi Cluster Indexing Preparation - II](https://github.com/livingdocsIO/livingdocs-server/pull/3348)
  * [Multi Cluster Indexing](https://github.com/livingdocsIO/livingdocs-server/pull/3361)
  * [Support Disabling Elasticsearch Clusters](https://github.com/livingdocsIO/livingdocs-server/pull/3373)
  * [Improve CLI Help for Indexing](https://github.com/livingdocsIO/livingdocs-server/pull/3371)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/commit/5d7d2622b937b69c132ddab653383efcf18e945c#diff-7bbdd5c871b81a390b45235abfd10ec146307fd2f4ebca354f4d2a1115b17a7c)


## Tracing :tada:

We've added tracing support in the server based on opentelemetry.

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3205)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/381)


## Support Deep Links in Multi Project Environments :tada:

We changed editor urls to contain the project handle so links work reliably in multi-project setups. This is the new pattern - `https://0.0.0.0:9000/p/<your-project-handle>/articles/<article-id>`

References:
  *  [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4171)


## Admin UI - Extend Indexing UI to Support all Configured Indexes :tada:

A server admin can now reindex every existing index.

![image](https://user-images.githubusercontent.com/431376/108784781-64a11f80-7570-11eb-92eb-7e3604c7b330.png)

References:
  *  [Editor PR](https://github.com/livingdocsIO/livingdocs-server/pull/3409)


### Support OpenID Connect for SSO

We support now OpenID Connect for a SSO connection. This allows customers to setup 2-factor authentication and external group management.

References:
- [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3355)
- [Documentation](https://github.com/livingdocsIO/livingdocs/pull/353)


# Breaking Changes :fire:

This time we have a rather high amount of breaking changes, therefore we grouped the breaking changes into different sections:
- [Post Deployment](#post-deployment-fire)
- [Breaking Changes - Public API](#breaking-changes---public-api-fire)
- [Breaking Changes - Server + Editor](#breaking-changes---server-+-editor-fire)
- [Breaking Changes - Server](#breaking-changes---server-fire)
- [Breaking Changes - Editor](#breaking-changes---editor-fire)


## Post Deployment :fire:

:fire: **Attention**, in this release we clean up some data structures to have better options for the future.
This section contains tasks you have to do **after** the deployment was successful and the new version is running properly.


### Revision Migration (post deployment) :fire:

We changed the `doc-link` and `doc-html` directives to be objects instead of strings (see [here](#changed-doc-link-and-doc-html-directive-to-objects-post-deployment-fire) to compare the :fire: old/new format).

After the deployment (when everything is running fine again) you should run the task :fire: `npx livingdocs-server revision-migration -t doc-link-and-doc-html -y`. This migrates all old revisions to use the new data format.

The default revision migration is quite slow and can be run in production without any impact. The revision migration should be run through all stages of deployment (dev, stage, prod). If you want to choose a more agressive approach outside of business hours, you can change the scheduler settings in the server config.

```js
// server config for a more agressive but more performant approach (should not be done during business hours)
documentMigration: {
   scheduler: {
        batchSize: 100, // default: 100
        concurrency: 10, // default: 1
       }
    }
}
```

:fire: Please make sure that all code that consumes Livingdocs (web frontend, native apps, etc.) support :fire: **both formats** and are still working as expected.

References:
- [Revision Migration Framework](https://github.com/livingdocsIO/livingdocs-server/pull/3268)
- [doc-link and doc-html Migration](https://github.com/livingdocsIO/livingdocs-server/pull/3398)
- [Set sane defaults for the Revision Migration](https://github.com/livingdocsIO/livingdocs-server/pull/3478)


### Migrate References (post deployment) :fire:

As described in the [APIs](#apis-gift) section, we extend some endpoints (public API + server API) with reference information of a document. Old document references need to be converted into the new format with a manual db migration.

After the release, execute the manual db migration `node ./db/manual-migrations/006-generate-references`

These are the key changes/issues
- It's a database heavy operation and should be executed outside business time (when having a lot of documents)
- The migration removes references from document revisions and stores them per document instead
- The migration generates references on all publications

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3341)


### CLI Script to Fix Group Memberships (post deployment) :fire:

We're having some customers running an old state of the groups tables which got partially corrupted by some old user merge logic that we've fixed about a year ago. The new `release-2021-03-fix-group-memberships` command fixes those tables completely.

- :fire: Run `npx livingdocs-server release-2021-03-fix-group-memberships` to fix corrupt membership data

References:
- [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3418)
- [Server Update PR](https://github.com/livingdocsIO/livingdocs-server/pull/3480)



## Breaking Changes - Public API :fire:

### Webhook Payload Change (publish/unpublish) :fire:

- :fire: Document publish webhook, changed value of `event` from `document.published` to `document.publish`
- :fire: Document unpublish webhook, changed value of `event` from `document.unpublished` to `document.unpublish`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3359)



## Breaking Changes - Server + Editor :fire:

### Changed doc-link and doc-html directive to objects :fire:

- :fire: Update [Framework](https://github.com/livingdocsIO/livingdocs-framework/pull/509) to v18 - New documents will store link and html directives as objects. Old documents will still store them as strings until you run the [manual migration](#revision-migration-post-deployment-fire).
- :fire: Public API: `GET /latestPublication` and `GET /latestPublications` return the JSON as stored in the database. Thus after the update you will receive the old and new format until you run the [manual migration](#revision-migration-post-deployment-fire).

After the update newly created doc-link and doc-html directives are stored as

```js
// Example Old
content = [{
  id: 'doc-ez23k2',
  identifier: 'design.link',
  content: {
    link: 'https://livingdocs.io'
  }
}, {
  id: 'doc-iej286',
  identifier: 'design.html',
  content: {
    html: '<div></div>'
  }
}]


// Example New
content = [{
  id: 'doc-ez23k2',
  identifier: 'design.link',
  content: {
    link: {
      href: 'https://livingdocs.io'
    }
  }
}, {
  id: 'doc-iej286',
  identifier: 'design.html',
  content: {
    html: {
      html: '<div></div>',
      target: '_blank'
    }
  }
}]
```


- 🔥 `getContent()` of html and link directives changes return type

The html and link directives are now data directives, i.e. store object literals. This means that the `getContent()` method will return an object literal and not a string value anymore. The change looks as follows.

```js
// old
const html = htmlDirective.getContent()
const href = linkDirective.getContent()

// new
const {html} = htmlDirective.getContent()
const {href, target} = linkDirective.getContent()
```

:fire: This change requires you to change all cases of `getContent` on link and html directives in your code. In particular look out for custom document conversions and include code.

If you used direct JSON access in a livingdoc directive (not recommended),
you will also need to change the access.

```js
// old
const html = htmlDirective.content.value
const href = linkDirective.content.value

// new
const {html} = htmlDirective.content
const {href, target} = linkDirective.content
```


References:
* [Framework PR](https://github.com/livingdocsIO/livingdocs-framework/pull/509)
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3242)
* [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3981)


### Use One Time Rendering by Default :fire:

The CheerioHtml output renderer for the render-pipeline now uses the frameworks one time rendering
by default which is 10 to 20 times faster but has a few minor differences in render output.

Things which are not rendered anymore by default:

- empty image classes
- empty optional elements (with display: none style)
- comments for hidden optional elements
- placeholders in unresolved include elements

You can still use the old renderer with `CheerioHtml({useLegacyRendering: true})` in your `contentType` configuration.

If you use custom outputFormatters which use the frameworks rendering you should switch them to `livingdoc.render()`. This gives you a big performance boost (10x - 20x faster) and ensures consistency with the new default of the CheerioHtml output renderer.


```js
// current - slow
html = rendition.livingdoc.toHtml()

// better alternative - fast
html = rendition.livingdoc.render()
```

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3401)



## Breaking Changes - Server :fire:

### Require npm7 :fire:

:fire: To support ~lib requires in downstreams we expect `npm > 7`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3475)

### Migrate the database :fire:

It's a simple/fast migration with no expected data losses.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 148-add-documents-project-id-not-null.js
#   add index on media_library_entries.media_type_id
# migration - 149-declare-expect_equal_version-as-immutable.js
#   update function expect_equal_version
# migration - 150-drop-legacy-tables.js
#   drop old tables assets / access_tokens / category_events / import_hugo_feeds
# migration - 151-add-references-columns.js
#   add column documents.references document_publications.references
# migration - 152-add-index-on-document-publications-created-at.js
#   add index on document_publications.created_at
# migration - 153-add-media-library-refs.js
#   add column media_library_entries.references
# migration - 154-add-index-on-authorization-code-events-aggregate-id.js
#   add index on authorization_code_events.aggregate_id
# migration - 155-add-content-type-id-on-document-publication-events.js
#   add column document_publication_events.content_type_id
# migration - 155-add-document-user-relations.js
#   add table document_user_relations
livingdocs-server migrate up
```


### Remove Legacy Postgres Tables :fire:

These Postgres tables have been removed:
- `assets` - got replaced by `media_library_entries` earlier last year
- `access_tokens` - The access_tokens table got removed in release-2020-12 as we now only track session ids
- `category_events` - This table wasn't in use at all
- `import_hugo_feeds` - This table also got created about 4 years ago and isn't in use

:fire: Please make sure that you don't directly access those tables in your code.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3386)


### Remove Grunt Tasks :fire:

Removed all Grunt tasks. If you still need a task, you can just copy the code to your downstream. But almost all functionality has been replaced with `livingdocs-server` CLI and the editor administration UI.
Please give us some feedback when you miss some functionality of a Grunt task, so we can provide that in the future in another form.

- 🔥 remove `grunt channel-create`
- 🔥 remove `grunt channel`
- 🔥 remove `grunt data-migration-create-and-prepare`
- 🔥 remove `grunt data-migration-accept`
- 🔥 remove `grunt data-migration-list`
- 🔥 remove `grunt data-migration-get`
- 🔥 remove `grunt data-migration-cancel`
- 🔥 remove `grunt data-migration-resume-all`
- 🔥 remove `grunt data-migration-get-report`
- 🔥 remove `grunt data-migration-list-errors`
- 🔥 remove `grunt data-migration`
- 🔥 remove `grunt list-create`
- 🔥 remove `grunt list-edit`
- 🔥 remove `grunt list`
- 🔥 remove `grunt project-create`
- 🔥 remove `grunt project`
- 🔥 remove `grunt user-authenticate`
- 🔥 remove `grunt user-password`
- 🔥 remove `grunt user-password-lock`
- 🔥 remove `grunt user-email`
- 🔥 remove `grunt user-edit`
- 🔥 remove `grunt user-create`
- 🔥 remove `grunt user-create-admin`
- 🔥 remove `grunt user-delete`
- 🔥 remove `grunt user`
- 🔥 remove `grunt webhook-subscribe`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3399)


### Changed API for indexingApi :fire:

- :fire: Removed `indexingApi.bulk`. The index clients are directly exposed in the index init features and on there we have a `esClient.customBulk` method you can use.
- :fire: `indexingApi.document.addDocumentUpdate` moved to `indexingApi.addDocumentUpdate`
- :fire: `indexingApi.document.reindex` got replaced by `indexingApi.addBackgroundIndexingJobsByBatches`
- :fire: `indexingApi.document.addJob` got removed. Please use `indexingApi.addBackgroundIndexingJobsByBatches` instead
- :fire: `indexingApi.media.addMediaUpdate` moved to `indexingApi.addMediaUpdate`
- :fire: `indexingApi.media.reindex` got replaced by `indexingApi.addBackgroundIndexingJobsByBatches`
- :fire: The cli tasks `es-media-reindex` and `es-search-reindex` got replaced by `elasticsearch-index`
  ```bash
  livingdocs-server elasticsearch-index --handle li-media
  livingdocs-server elasticsearch-index --handle li-documents
  livingdocs-server elasticsearch-index --handle li-publications
  ```
- :fire: Upgrade to [`pino@6.11.0`](https://github.com/pinojs/pino/releases/tag/v6.0.0)
  ```js
  // Previously, Pino supported multiple arguments and concatenated them into a string
  // With the upgrade, the api changed slightly and to form the same message, `%s` and `%j` must be used

  // Example 1
  //   Before
  log.info({foo: 'bar'}, 'a message', { an: 'object'})
  //   After
  log.info({foo: 'bar'}, 'a message %j', { an: 'object' })
  //   Output
  "foo":"bar","msg":"a message {\"an\":\"object\"}"


  // Example 2
  //   Before
  log.info({foo: 'bar'}, 'a', 'silly', 'message')
  //   After
  log.info({foo: 'bar'}, 'a %s %s', 'silly', 'message')
  //   Output
  "foo":"bar","msg":"a silly message"
  ```

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3361)

### Changed format of 'document.update' event :fire:

The `document.update` event will only receive `user: {id: userId}`. Previously the user object could have more params on it (like admin or project_id) depending on what user object was passed into documentApi.updateV2(). Note that currently it is also possible that `user: {id: undefined}` is passed as the user.id is not required in documentApi.updateV2().

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3352)

### Removed 'li-netlify-publish-hooks' feature :fire:

🔥 Removes the `li-netlify-publish-hooks` feature (which seems not to be used by anyone) as the more generic webhooks feature already offers the same behavior. The [webhook](https://docs.livingdocs.io/reference-docs/server-initalization/webhooks) documentation can help to migrate the feature.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3362)



### Add property 'isAutomatic' to Metadata plugin 'li-image' :fire:

A metadata field of type `li-image` has a new property `isAutomatic`, e.g. `teaserImage.crops[{..., isAutomatic: true}].`
:fire: Add the field `isAutomatic` to the Elasticsearch metadata mapping:

```js
// 1) search in the project config for all metadata fields with type 'li-image' (e.g. teaserImage)
// 2) Open the Elasticsearch mapping file defined in the server config 'search.metadataMapping' (see https://docs.livingdocs.io/reference-docs/server-config/config#search)
// 3) Update the mapping definition with 'isAutomatic' for all metadata fields of type 'li-image'

// metadata-mapping.js
{
    ...,
    "teaserImage": {
      "properties": {
        "crops": {
          "properties": {
            ...
            "isAutomatic": { // <------------    add isAutomatic property to the mapping
              "type": "boolean"
            }
          }
        }
      }
    }
}
```

:fire: removed the editor config `app.ui.article.publish.cropStyles`. It has no effect anymore

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4051)

### Upload Media Assets via Streams instead of a Buffer :fire:

- :fire: removed `mediaLibraryApi.addImageCb`, use `mediaLibraryApi.addImage` (promise) instead
- :fire: changed `mediaLibraryApi.addImages({..., tempBase64})` to `mediaLibraryApi.addImages({..., stream})` (pass an image stream for an exif extraction)
- :fire: `imagesApi.processJob` does not support callbacks anymore
- :fire: changed `designsApi.write.uploadAsset({..., file})` to `designsApi.write.uploadAsset({..., readStream})`. Instead of passing a `buffer` you have to pass a `readStream`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3396)

### Include Api Refactoring :fire:

- 🔥 `includeApi.registerService()` We're sunsetting of the old service config format which used ui and server properties instead of the new format with uiComponents and rendering. This format has been deprecated with a logged warning for a few years now. If the server starts successfully you don't use the old format.
- 🔥 Removed `includeApi.resolveChannelOutputs()` (but this function should only have been used internally)

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3405)

### Group Api - Optimistic Locking :fire:

:fire: `groupApi.updateGroup({..., version})` - version changed the optimistic locking behavior. Previously when doing an update against a group, the version must have been +1 of the state on the server. When doing requests from now on, the version in the request must match the version on the server.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3449)

### Woodwing Asset Api :fire:

:fire: removed url from `woodwingAssetsApi.uploadImageToWoodwingAssets({..., url})` and added stream (readStream) `woodwingAssetsApi.uploadImageToWoodwingAssets({..., stream})`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3437)

### Media Library Filter :fire:

- 🔥 Media Library Index: `caption`, `source` and `google-vision` fields are not indexed automatically anymore. The config `config: {index:true}` must be set in the metadata configuration.

```js
// When you still want to search/filter by caption or source or google-vision, you have to extend your mediaType config in the project config
{
  metadata: [
    {
      handle: 'source', // or 'caption' or 'google-vision'
      // ...
      config: {
        index: true, // <------- add this property to be able to search/filter
      }
    },
    // ...
  ]
}
```

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3389)





## Breaking Changes - Editor :fire:

### Fix close tags in Angular templates :fire:

:fire: If you have downstream **Angular** templates, change all XHTML like closing tags `<some-tag/>` to valid HTML5 `<some-tag></some-tag>`.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4107)

### Media Library Dashboard Configuration Change :fire:

:fire: Removed project config `editorSettings.mediaLibrary.editorSelection.displayFilters`

If you want to keep the filters, you need to move the config to the `mediaType` project config.

```js
// mediaType config example
{
  handle: 'image',
  type: 'mediaImage',
  metadata: [],
  editor: {
    dashboard: {
      // use the config of editorSettings.mediaLibrary.editorSelection.displayFilters
      // if you want to keep the old behavior
      displayFilters: []
    },
    managementDashboard: {
      // configure different filters for the management dashboard (opened via Main Navigation)
      // if you want.
      displayFilters: []
    }
  }
}
```

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4106)


### Prefix all app Routes with a Project Handle :fire:

#### Rename UI Router Application States 'app' -> 'project'
🔥 We renamed all ui router application states. All states for the editor routing are affected.
Examples, where it could be used in customer projects are:
- `ui-sref`
- `$state.go('')`
- `state.$href`
- or within the project config the `mainNavigation` may also be affected if it uses editor states instead of urls.

In most cases this is the easy migration guide for almost all states prefixed with 'app.*'
**Before**: `$state.go('app.welcome')`
**After**: `$state.go('project.welcome')`

_Note: Exception are server admin routes route like 'app.admin.users' is still 'app.admin.users' and user routes like 'app.user'_


#### Rename Project Routes/States

:fire: Changed url schema from `/projects/id/*` to `/p/projectHandle/config/*`
```js
// Example
https://0.0.0.0:9000/projects/111/settings           // from
https://0.0.0.0:9000/p/e2e-magazine/config/settings  // to
```

:fire: Changed state from `app.settings*` to `project.config*`
```js
// Example
return this.$state.go('project.settings.contentType.content')   // from
return this.$state.go('project.config.contentType.content')     // to
```

:fire: Changed url schema from `/access/id/*` to `/p/projectHandle/admin/*`
```js
// Example
https://0.0.0.0:9000/access/111/members            // from
https://0.0.0.0:9000/p/e2e-magazine/admin/members  // to
```

:fire: Changed state from `app.access*` to `project.admin*`
```js
// Example
return this.$state.go('project.access.current.groups')   // from
return this.$state.go('project.admin.current.groups')    // to
```

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4171)


### Drop Coffee Script Support :fire:

- 🔥 Remove coffee-script support in the webpack setup in the editor. We've dropped coffee-script a few years ago, but still kept the webpack loader as not all projects were migrated. From now on we've completely removed support for it. Please upgrade your code base if you still use coffee-script.

If you still want to use coffeescript, you can require it manually, e.g. `node -r coffee-cscript/register node index.js`.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4164)

### Remove Deprecated Editor Env Config 'dashboards' :fire:

- :fire: remove [deprecated](https://github.com/livingdocsIO/livingdocs-editor/pull/3663) editor config `dashboards`.

```js
// editor config - old
module.exports = {dashboards: [{handle: 'kanban-proofreading'}]}

// project config - new
projectConfig.editorSettings.dashboards: [{handle: 'kanban-proofreading'}]`
```

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4166)


### liDateTimeRange Filter config :fire:

- :fire: `metadataPropertyName` in the liDateTimeRange Filter config can only be used for metadata. To filter for `documentPropertyName` created_at or updated_at (default) you should use in the config `{filterName: 'liDateTimeRange', config: {documentPropertyName: 'updated_at'}}`

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4202)


# Deprecations

## Node 12 Support

💣 Node 12 is deprecated. Please upgrade your docker images and local environments to node 14.

This follows our upgrade cycle that we drop the old lts version one year after the introduction of the [current LTS version](https://nodejs.org/en/about/releases/).

In your docker images change
- `FROM livingdocs/server-base:12` to `FROM livingdocs/server-base:14` or `:15`
- `FROM livingdocs/editor-base:12` to `FROM livingdocs/editor-base:14` or `:15`
- `FROM livingdocs/node:12` to `FROM livingdocs/node:14` or `:15`

In your `.nvmrc` (if present) change
- The string from `12` to `14` or `15`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3442)


## swisscomTV.customLanguageHandle

The server config `swisscomTV.customLanguageHandle` is not used any longer for the reference extraction. All metadata of type `li-language` will be extracted to the references if they have a `groupId`.

## Server Callbacks

All callback functions on the server are now in deprecated state. We will start removing callbacks and switch to a promise based only approach.




# APIs :gift:

## Publication Events

- :candy: Support `/api/v1/publicationEvents?reverse=true` query parameter to retrieve events in reverse order starting at the latest event

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3447)
* [Documentation](https://github.com/livingdocsIO/livingdocs-editor/pull/4290)

## References

We worked on document reference extraction. The list below contains public APIs and server APIs with an additional `reference` property in the response. Look into the [documentation](https://github.com/livingdocsIO/livingdocs/pull/372) to get different types of references. References can be used for static page rendering strategies where updates of references in a page, e.g. teasers, must be identified.

- :candy: `POST /document-copy/:documentId/copy`
- :candy: `POST /document-copy/:documentId/transform`
- :candy: `POST /publications/:publicationId/republish`
- :candy: `documentApi.getLatestDocument()`
- :candy: `documentCopyApi.copyByDocumentId()`
- :candy: `documentCopyApi.copyWithoutConfig()`
- :candy: `documentCopyApi.transformByDocumentId()`
- :candy: `publicationApi.getLatestPublication()`
- :candy: `publicationApi.getLatestPublications()`
- :candy: `publicationApi.getPublicationsByDate()`
- :candy: `publicationApi.getPublicationsByDocumentIds()`
- :candy: `publicationApi.republish()`

References:
* [Documentation](https://github.com/livingdocsIO/livingdocs/pull/372)
* [Extract References PR](https://github.com/livingdocsIO/livingdocs-server/pull/3341)
* [Extract References for Videos PR](https://github.com/livingdocsIO/livingdocs-server/pull/3383)
* [Add Endpoints PR](https://github.com/livingdocsIO/livingdocs-server/pull/3365)


## Public API - Add context object to import endpoints :gift:

A `context` (max 8192 bytes) parameter can be passed to:

- `POST api/v1/import/documents`
- `POST api/v1/import/images`
- `POST api/v1/import/videos`

If the webhook parameter is defined as well, context will be passed to the webhook once the job is finished.

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs-editor/pull/4100)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3353)


## Public API - Add Media Library Webhooks + Extend document.update Webhook :gift:

- 🎁 Add webhook for event `mediaLibraryEntry.create`
- 🎁 Add webhook for event `mediaLibraryEntry.update`
- 🎁 Add webhook for event `mediaLibraryEntry.archive`
- :candy: Extend `document.update` webhook - subscribe to a specific metadata property update

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/367)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3359)


## Public API Beta

For all public API endpoints documentation, go to 'https://your-editor.com/public-api'.

- 🎁 Add new endpoint `GET /api/beta/documents/:documentId/incomingDocumentReferences`
- :candy: `GET /api/beta/documents/:documentId/latestPublication` - add next extracted references format
- :candy: `GET /api/beta/documents/:documentId/latestPublications` - add next extracted references format
- 🎁 Add new endpoint `GET /api/beta/documents/:documentId/incomingMediaReferences`
- 🎁 Add new endpoint `GET /api/beta/mediaLibrary/:mediaId/incomingDocumentReferences`
- 🎁 Add new endpoint `GET /api/beta/mediaLibrary/:mediaId/incomingMediaReferences`

References:
* [Documentation](https://github.com/livingdocsIO/livingdocs-editor/pull/4228)
* [Add Endpoints PR I](https://github.com/livingdocsIO/livingdocs-server/pull/3365)
* [Add Endpoints PR II](https://github.com/livingdocsIO/livingdocs-server/pull/3400)


## Server API - includesApi

- :gift: Add `includesApi.getServiceConfig({serviceName})` method to `includesApi`.



# Internal Changes

## Colt

```js
// Simple import of all colt factories
const {colt} = require('../support/factories')
// --> instead of require('../support/factories').get('user', 'project', 'channel', 'document', 'publication')


// New Test Helper to create a configurable Project.
colt().createConfigProject('project', {...})
```


# Other Changes

### Features

* Tasks: Assign a user to a task [livingdocs-editor #4214](https://github.com/livingdocsIO/livingdocs-editor/pull/4214) :gift:
* Print: Move print to project config [livingdocs-server #3372](https://github.com/livingdocsIO/livingdocs-server/pull/3372) :gift:

### Design

* Priority truck polish [livingdocs-editor #4091](https://github.com/livingdocsIO/livingdocs-editor/pull/4091) :gift:
* Style Guide: Clean up the style guide [livingdocs-editor #4149](https://github.com/livingdocsIO/livingdocs-editor/pull/4149) :gift:
* Improve dashboard footer [livingdocs-editor #4209](https://github.com/livingdocsIO/livingdocs-editor/pull/4209) :gift:

### Improvements

#### Editor

* Dashboards
  * Properly handle pagination for a resultList [livingdocs-editor #4153](https://github.com/livingdocsIO/livingdocs-editor/pull/4153) :gift:
  * List dashboard: Hide 'go to article' button in list UI when dragging [livingdocs-editor #4094](https://github.com/livingdocsIO/livingdocs-editor/pull/4094) :gift:
  * Add 'video-' and 'imageLibrary' dashboard [livingdocs-editor #4046](https://github.com/livingdocsIO/livingdocs-editor/pull/4046) :gift:
* Search
  * Add support for a `customFilters` object to pass through custom search parameters [livingdocs-editor #4172](https://github.com/livingdocsIO/livingdocs-editor/pull/4172) :gift:
* Image cropping: Use downscaled image size for very large images [livingdocs-editor #4141](https://github.com/livingdocsIO/livingdocs-editor/pull/4141) :gift:
* Editing: Add Iframe height watcher (guard) [livingdocs-editor #4108](https://github.com/livingdocsIO/livingdocs-editor/pull/4108) :gift:

#### Media Library

* Media Upload/Import
  * Remove hardcoded mediaTypes [livingdocs-editor #4155](https://github.com/livingdocsIO/livingdocs-editor/pull/4155) :gift:
  * Simplify code [livingdocs-server #3369](https://github.com/livingdocsIO/livingdocs-server/pull/3369) :gift:
  * Allow multiple mediaTypes of same type, allow mediaType parameter for upload/import APIs [livingdocs-server #3406](https://github.com/livingdocsIO/livingdocs-server/pull/3406) :gift:
  * Hardening Media Library Import [livingdocs-server #3430](https://github.com/livingdocsIO/livingdocs-server/pull/3430) :gift:
  * Reimplement `video.asset.size` support for the stream-based upload [livingdocs-server #3439](https://github.com/livingdocsIO/livingdocs-server/pull/3439) :gift:
* Resolve dashboards in Main Navigation and Document Editing Toolbar from mediaTypes config [livingdocs-editor #4106](https://github.com/livingdocsIO/livingdocs-editor/pull/4106) & [livingdocs-editor #4180](https://github.com/livingdocsIO/livingdocs-editor/pull/4180) :gift:

#### Other

* CLI: Add 'newerThan' argument for task 'cleanup-documents' [livingdocs-server #3333](https://github.com/livingdocsIO/livingdocs-server/pull/3333) :gift:
* Import: Support files with no file ending of mimeType image [livingdocs-server #3380](https://github.com/livingdocsIO/livingdocs-server/pull/3380) :gift:
* Error handling: Add extended description to error declaration class [livingdocs-server #3214](https://github.com/livingdocsIO/livingdocs-server/pull/3214) :gift:
* Add Support for Secure Imgix URLs [livingdocs-server #3410](https://github.com/livingdocsIO/livingdocs-server/pull/3410) :gift:
* Includes
  * Add interaction blocker config option [livingdocs-server #3397](https://github.com/livingdocsIO/livingdocs-server/pull/3397) :gift:
  * Add interaction blocker to project config to include services UI [livingdocs-editor #4205](https://github.com/livingdocsIO/livingdocs-editor/pull/4205) :gift:
* Security: Revoke client if another user uses the same client id [livingdocs-server #3441](https://github.com/livingdocsIO/livingdocs-server/pull/3441) :gift:
* Filter: allow document_types to be an array [livingdocs-server #3412](https://github.com/livingdocsIO/livingdocs-server/pull/3412) :gift:


### Bugfixes

* Media library
  * Rename pusher topic to media and allow - in mediaId [livingdocs-server #3382](https://github.com/livingdocsIO/livingdocs-server/pull/3382) :beetle:
  * Video: Use video public URL and not image public URL [livingdocs-editor #4048](https://github.com/livingdocsIO/livingdocs-editor/pull/4048) :beetle:
* Access Management: Groups - hide iMatrics for projects that don't use it [livingdocs-editor #4062](https://github.com/livingdocsIO/livingdocs-editor/pull/4062) :beetle:
* Metadata: Correctly handle image URL's when picking from article [livingdocs-editor #4132](https://github.com/livingdocsIO/livingdocs-editor/pull/4132) :beetle:
* Editor Link Tool: fix link validation / update link info / no reload on enter [livingdocs-editor #4142](https://github.com/livingdocsIO/livingdocs-editor/pull/4142) :beetle:
* Comments: Fix comment highlight when paging through comment cards [livingdocs-editor #4147](https://github.com/livingdocsIO/livingdocs-editor/pull/4147) :beetle:
* Fix Image Cropper on Mobile [livingdocs-editor #4175](https://github.com/livingdocsIO/livingdocs-editor/pull/4175) :beetle:
* Guard projects from having a undefined handle in the url [livingdocs-editor #4182](https://github.com/livingdocsIO/livingdocs-editor/pull/4182) :beetle:
* Editor: Fix transform components feature [livingdocs-editor #4219](https://github.com/livingdocsIO/livingdocs-editor/pull/4219) :beetle:
* Comments: Show max thread count limit error [livingdocs-editor #4188](https://github.com/livingdocsIO/livingdocs-editor/pull/4188) :beetle:

### Service

* Public Api: downgrade contentFormat when required [livingdocs-server](https://github.com/livingdocsIO/livingdocs-server/pull/3468) :gift:


  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:

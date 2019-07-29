
# saved-search-watcher - Alert on Kibana Saved Searches using Elasticsearch Watcher

Using a search template, the `toJson` Mustache template tag, the search `meta`
attribute, and a Saved Search, a Watcher can be implemented which will use the
Apache Lucene style query from the Saved Search.

This repository provides a concreate example of this method.

[NoSpaceships][nospaceships] has released this project under the terms of the
MIT license.

If you have any issues or feedback, or would like to discuss any requirements
you may have, please [contact us][contact-us].

The [saved-search-watcher blog][saved-search-watcher-blog] post on the
NoSpaceships website provides a comprehensive run through of how the Watcher is
pieced together, and why each element is required.

# Using the Example

The example Watcher exists in the `saved-search-watcher.json` file.

Navigate to the Dev Tools in the Kibana UI, and use the following request to
add the Watcher - pasting the contents of the above file in place of `{...}`:

    PUT _pack/watch/watcher/system-log-errors
    {...}

The Watcher will then be live.

To use the Watcher for specific use cases, review the following:

 * The `savedSearchId` attribute under the `metadata` attribute - Set this to
   be the ID of the Saved Search which should be used.
 * The `name` attribute under the `metadata` attribute - Set this to
   be the Watcher name.
 * Update the `search.request.indices` attribute under the `savedSearchQuery`
   input in the Watcher.
 * Review the Watchers actions, specifically, the `send_email` action, replace
   or update this as required.

# Changes

## Version 1.0.0 - 29/07/2019

 * Initial version

# License

Copyright 2019 NoSpaceships Ltd

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[contact-us]: mailto:hello@nospaceships.com?subject=saved-search-watcher
[nospaceships]: https://nospaceships.com
[saved-search-watcher-blog]: https://www.nospaceships.com/2019/07/29/alert-on-kibana-saved-searches-with-elasticsearch-watcher.html

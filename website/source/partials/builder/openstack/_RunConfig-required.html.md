<!-- Code generated from the comments of the RunConfig struct in builder/openstack/run_config.go; DO NOT EDIT MANUALLY -->

-   `source_image` (string) - The ID or full URL to the base image to use. This is the image that will
    be used to launch a new server and provision it. Unless you specify
    completely custom SSH settings, the source image must have cloud-init
    installed so that the keypair gets assigned properly.
    
-   `source_image_name` (string) - The name of the base image to use. This is an alternative way of
    providing source_image and only either of them can be specified.
    
-   `source_image_filter` (ImageFilter) - Filters used to populate filter options. Example:
    
    ``` json {
        "source_image_filter": {
            "filters": {
                "name": "ubuntu-16.04",
                "visibility": "protected",
                "owner": "d1a588cf4b0743344508dc145649372d1",
                "tags": ["prod", "ready"],
                "properties": {
                    "os_distro": "ubuntu"
                }
            },
            "most_recent": true
        }
    }
    ```
    
    This selects the most recent production Ubuntu 16.04 shared to you by
    the given owner. NOTE: This will fail unless *exactly* one image is
    returned, or `most_recent` is set to true. In the example of multiple
    returned images, `most_recent` will cause this to succeed by selecting
    the newest image of the returned images.
    
    -   `filters` (map of strings) - filters used to select a
    `source_image`.
        NOTE: This will fail unless *exactly* one image is returned, or
        `most_recent` is set to true. Of the filters described in
        [ImageService](https://developer.openstack.org/api-ref/image/v2/), the
        following are valid:
    
        -   name (string)
    
        -   owner (string)
    
        -   tags (array of strings)
    
        -   visibility (string)
    
        -   properties (map of strings to strings) (fields that can be set
            with `openstack image set --property key=value`)
    
    -   `most_recent` (boolean) - Selects the newest created image when
    true.
        This is most useful for selecting a daily distro build.
    
    You may set use this in place of `source_image` If `source_image_filter`
    is provided alongside `source_image`, the `source_image` will override
    the filter. The filter will not be used in this case.
    
-   `flavor` (string) - The ID, name, or full URL for the desired flavor for the server to be
    created.
    
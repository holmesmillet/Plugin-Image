Statamic Image Plugin
================================

The Image plugin is used for resizing, cropping, and manipulating your images on the fly, right from your template code. All images are cached and timestamped so caches are refreshed when files update.

## Installing
1. Download the zip file (or clone via git) and unzip it or clone the repo into `/_add-ons/`.
2. Ensure the folder name is `image` (Github timestamps the download folder).
3. Enjoy.

## Example Tag

    {{ image src="/url_path/to/image" dim="400x300" }}
      <img src="{{ image_url }}" width={{ width }} height={{ height }} />
    {{ /image }}

## Parameters

### Quality `quality`

Pass an integer from 1 to 100 to set your desired quality.

    quality="80"

### Dimension `dim`
The dimension parameter is a swiss-army knife, all-in-one style parameter. Pass it your width x height (WxH), and your resize/crop flag and you're done.

    dim="400x300>"

#### Resize/Crop Flags

**WxH#**

Center Crop to W/H, new image will be WxH, sized up if necessary

For example, with an image that is 150x150px and `dim=400x200#`, the image would be scaled up to 400x400 and then center cropped to fit 400x200

**WxH!**

Rescale the image to W/H. For example, with an image that is 150x150px and `dim=400x200!`, the image would be scaled to 200px high and by 400px wide

**WxH<**

Image will be rescaled to fit W/H with a fixed **width**

**WxH>**

Image will be rescaled to fit W/H with a fixed **height**

**WxH(**

Image will be cropped to fit W/H with a fixed **width**

**WxH)**

Image will be cropped to fit W/H with a fixed **height**

## Variables

### Image URL `{{ image_url }}`

The processed and cached image URL to reference.

### Width `{{ width }}`

The final width of the image

### Height `{{ height }}`

The final width of the image

## Parse Mode

## Example Parse Tag

    {{ image content='{content}' dim="400x300<" }}

Example Input

    <img src="/fish.jpg">

Example Output

    <img src="_cache/assets/img/blog/400x300a2-fish.jpg">

## Parameters

### Content `content`

Pass content from a wysiwyg field or any text field containing html.

    content='{content}'
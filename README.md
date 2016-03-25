# AppleNewsFormat
Sample JSON for Apple News Format

To preview [Apple News Format](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/index.html#//apple_ref/doc/uid/TP40015408-CH79-SW1) files install [News Preview](https://developer.apple.com/news-preview/).

Note: You'll also need [Xcode](https://itunes.apple.com/gb/app/xcode/id497799835?mt=12) installed for it to work because it borrows the iOS simulators.

Presented here are a range of stripped back JSON files that should assist you in constructing your own.

## Basic

A JSON file with the minimum required [properties](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Properties.html#//apple_ref/doc/uid/TP40015408-CH2-SW1). The components array should have at least one [component](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Component.html#//apple_ref/doc/uid/TP40015408-CH5-SW1) to be valid but the [componentTextStyles](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/ComponentTextStyle.html#//apple_ref/doc/uid/TP40015408-CH58-SW1) dictionary can be left empty.

## Component Text Styles

You can add text styles by first referencing them with a textStyle key inside a [component](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Component.html#//apple_ref/doc/uid/TP40015408-CH5-SW1) and then adding a [componentTextStyle](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/ComponentTextStyle.html#//apple_ref/doc/uid/TP40015408-CH58-SW1) of the same name to the componentTextStyles dictionary. Think of component text styles as paragraph styles for your text, they can be reused time and again.

Note: The fonts you employ can be chosen from the [entire list of iOS fonts](http://iosfonts.com). Although it is possible to [include custom fonts](http://stackoverflow.com/questions/33745629/add-a-custom-font-to-apple-news/36187801#36187801) there don't appear to be any guidelines on whether you should.

## Markdown

Once you have the [basic structure](https://gist.github.com/sketchytech/512d242e38d085ad8648) in place for your [Apple News Format](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/index.html#//apple_ref/doc/uid/TP40015408-CH79-SW1) article, and the [component text styles](https://gist.github.com/sketchytech/6c5ff4be95b2f0ef70ab) for your paragraph style formatting, you can then use either [markdown](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Markdown.html#//apple_ref/doc/uid/TP40015408-CH85-SW1) or [inline text styles](https://gist.github.com/sketchytech/c06513e115a91e2a0d6a) for local formatting. To use markdown in any of your components simply add a `format` key with the value `markdown`.

Note: markdown is only applied to components that have a [component text style](https://gist.github.com/sketchytech/6c5ff4be95b2f0ef70ab) and when you have markdown applied all [inline text styles](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/InlineTextStyle.html#//apple_ref/doc/uid/TP40015408-CH64-SW1) are ignored for that component.

## Inline Text Styles

You can use either [markdown](https://gist.github.com/sketchytech/8134a3a4089fcf592606) or [inline text styles](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/InlineTextStyle.html#//apple_ref/doc/uid/TP40015408-CH64-SW1) for local formatting. To use markdown in any of your components simply add a **format** key with the value **markdown**. To use inline [text styles](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/TextStyle.html#//apple_ref/doc/uid/TP40015408-CH77-SW1) add an **inlineTextStyles** key to your text component, the value of which will be an array of inline text styles. 

Note: local styles are only applied to components that have a [component text style](https://gist.github.com/sketchytech/6c5ff4be95b2f0ef70ab) and when you have markdown applied all [inline text styles](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/InlineTextStyle.html#//apple_ref/doc/uid/TP40015408-CH64-SW1) are ignored for that component.

## Text Styles

In order to separate out and repeat text styles, as you would with character styles in a word processor or typesetting app, you can use a **textStyles** key in the top level of your dictionary, the value of which is a dictionary holding a list of styles in a similar way to the **componentTextStyles** key.

Once you have a list of text styles these can be referenced by replacing the **textStyle** dictionary within you [inline styles](https://gist.github.com/sketchytech/c06513e115a91e2a0d6a) with a string referencing a key within the **textStyles** dictionary.

Note: local styles are only applied to components that have a [component text style](https://gist.github.com/sketchytech/6c5ff4be95b2f0ef70ab) and when you have markdown applied all [inline text styles](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/InlineTextStyle.html#//apple_ref/doc/uid/TP40015408-CH64-SW1) are ignored for that component.

## Document Style

[Document Style](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/DocumentStyle.html#//apple_ref/doc/uid/TP40015408-CH60-SW1) is an top-level optional property. At present a document style has only one option and that is to set the background colour using a hexadecimal string.

Note: **documentStyle** is a top-level key with a value that is a dictionary.

## Metadata

Metadata has 13 different keys. Aside from the important ones like **author** and **date**,  **thumbnailURL** and **canonicalURL** are of particular importance when your article is being shared through social media and **excerpt** is also highly recommended for where a synopsis of your article will appear.

Note: The **thumbnailURL** must point to a file contained within the same folder as your article json when previewing through [News Preview](https://developer.apple.com/news-preview/). And an **excerpt** must not contain markdown.

## Embed a tweet

You can embed a [tweet](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Tweet.html#//apple_ref/doc/uid/TP40015408-CH37-SW1) in your article by simply adding it to the components. Two properties are required: **role** and **URL** and there are five optional properties: **anchor**, **behavior**, **identifier**, **layout** and **style**.

Note: components are rendered in which they are listed.

## Link Addition

A [Link Addition](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/LinkAddition.html#//apple_ref/doc/uid/TP40015408-CH88-SW1) is the only type of addition thus far in the [Apple News Format](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/index.html). An array of additions is inserted inside a component in the same way as an array of [inline text styles](https://gist.github.com/sketchytech/c06513e115a91e2a0d6a) is.

A personal hope is that additions are added for pop-up notes and also index entries. This way we could move to make Apple News Format a great way to present journal articles and even construct books.

Note: Thanks go to [an answer](http://stackoverflow.com/a/36158820/1694526) I received  to a question posted on StackOverflow.

## Mosaic and Gallery Images

You can add images to it in a static [mosaic](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Mosaic.html#//apple_ref/doc/uid/TP40015408-CH26-SW1) or scrollable [gallery](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Gallery.html#//apple_ref/doc/uid/TP40015408-CH17-SW1) form. Both are objects placed within the [components](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Component.html#//apple_ref/doc/uid/TP40015408-CH5-SW1) array and contain an array of [gallery items](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/GalleryItem.html#//apple_ref/doc/uid/TP40015408-CH63-SW1). These gallery items can each include a URL that references an image (JPEG, PNG or GIF) inside the same folder as the `article.json` file, along with caption and voiceover information (accessibility caption), as well as an explicit content flag. (A Gallery Item has no required properties, only optional ones.)

There are a list of optional properties identical for mosaic and gallery: anchor, animation, behavior, identifier, layout and style. These are inherited from [Text(Abstract)](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Text.html#//apple_ref/doc/uid/TP40015408-CH35-SW1) and [Component(Abstract)](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Component.html#//apple_ref/doc/uid/TP40015408-CH5-SW1).

Tapping on an image expands it and displays the caption when inside Apple News.

## Column Layout

You can explore laying out your [components](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Component.html#//apple_ref/doc/uid/TP40015408-CH5-SW1) in columns. In order to do this you need to define a [layout at the top level](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Layout.html#//apple_ref/doc/uid/TP40015408-CH65-SW1) and a [layout within the body of components](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/ComponentLayout.html#//apple_ref/doc/uid/TP40015408-CH56-SW1). By default components span all columns.

## Scalable Images and Component Animations

The `role` for a scalable image is the type of image: [Figure](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Figure.html#//apple_ref/doc/uid/TP40015408-CH16-SW1), [Photo](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Photo.html#//apple_ref/doc/uid/TP40015408-CH28-SW1), or [Portrait](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Portrait.html#//apple_ref/doc/uid/TP40015408-CH30-SW1). There is also an [Image](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/Image.html#//apple_ref/doc/uid/TP40015408-CH21-SW1) component of which the only supported role is currently `logo`. As with [Gallery and Mosaic](https://gist.github.com/sketchytech/1aa9147e4d317d379b38) images, all images must be contained within the same folder as the `article.json` file and must be JPEG, PNG or GIF format. They are referenced as being in the bundle, e.g. `"URL": "bundle://image2.jpg"`

There are four types of [Component Animations](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/ComponentAnimation.html#//apple_ref/doc/uid/TP40015408-CH40-SW1): [Appear](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/AppearAnimation.html#//apple_ref/doc/uid/TP40015408-CH52-SW1), [Fade-in](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/FadeInAnimation.html#//apple_ref/doc/uid/TP40015408-CH62-SW1), [Move-in](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/MoveInAnimation.html#//apple_ref/doc/uid/TP40015408-CH68-SW1), [Scale Fade](https://developer.apple.com/library/ios/documentation/General/Conceptual/Apple_News_Format_Ref/ScaleFade.html#//apple_ref/doc/uid/TP40015408-CH72-SW1).

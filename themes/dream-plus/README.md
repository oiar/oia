# Dream Plus Theme for Hugo

![Dream Plus Theme](https://github.com/UtkarshVerma/hugo-dream-plus/blob/master/images/original.png)
This theme is an upgraded version of the [Dream Theme](https://github.com/g1eny0ung/hugo-theme-dream) by [Yue Yang](https://github.com/g1eny0ung) and contains tons of new features such as:

* "Card" and "Post" views for the home page
* twemoji rendering
* Table of contents for posts
* Random image background
* Multiple author support
* Disqus
* Sidebar
* Share card below posts
* Device detection, that is whether the client device is a PC or phone
* About section can be written in MarkDown
* Custom 404 pages can be written in MarkDown
* Custom Favicon
* RSS Button
* Custom CSS and JS can be used without modifying the theme
* More social icons
* Shorte.st website script, and a lot of other minor improvements

This theme can be used for two purposes:

1. If you're making a site which links to other sites and your stuff all around the internet, then you can switch to card view for that. I use this view for my home page here: [UtkarshVerma's Site](https://utkarshverma.me)
2. If you're simply making a blog or another website with a bunch of posts, then switch to the posts view for that. I use this view for my blog: [UtkarshVerma's Blog](https://blog.utkarshverma.me)

This project adheres to the Contributor Covenant [code of conduct](/CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to [utkarshverma@pm.me](mailto:utkarshverma@pm.me).


### Live Demo
* [**Cards View**](https://dream-plus-cards.netlify.com)
* [**Posts View**](https://dream-plus-posts.netlify.com)

---

## Table of Contents
* [**Installation**](#installation)

* [**Getting Started**](#getting-started)

* [**Documentation**](#documentation)

* [**Nearly Finished**](#nearly-finished)

* [**Contributing**](#contributing)

* [**License**](#license)

---

## Installation
The theme can be installed by running the following commands inside your **Hugo website** folder.
```shell
cd themes
git submodule add https://github.com/UtkarshVerma/hugo-dream-plus dream-plus
git submodule update --init --recursive
```

## Getting Started
Once the theme has been successfully installed, you'll have to do a bit of tuning of the theme to meet your taste.

### Configure Dream Plus
Within the [`exampleSite`](/exampleSite) folder, you'll find the config files, [`cards.toml`](/exampleSite/cards.toml) and [`posts.toml`](/exampleSite/posts.toml) which can be used to tweak the theme.

You must use these config files as a basis for your site, since they **take care of the necessary variable declarations**, which you may edit according to your needs.

### Describe yourself
Define yourself through the following config variables in `params`:
```toml
author = "<name of the author>"
description = "Short description of the site"
motto = "author's motto or short description"

#Leaving the avatar variable unset displays svg avatars
avatar = "<absolute path to avatar>"
```

After that, fill up the social variables at the end of the config file. This theme suports the following social sites: (The examples are given)

| Social Link | Variable | Example Initialization |
|:---:|:---:|:---:|
| GitHub | *github* | `github = "username"` |
| Email | *email* | `email = "username@example.com"` |
| Twitter | *twitter* | `twitter = "username"` |
| Facebook | *facebook* | `facebook = "username"` |
| YouTube | *youtube* | `youtube = "username"` |
| Medium | *medium* | `medium = "username"` |
| LinkedIn | *linkedin* | `linkedin = "username"` |
| StackOverflow | *stackoverflow* | `stackoverflow = "number/username"` |
| CodePen | *codepen* | `codepen = "username"` |
| Reddit | *reddit* | `reddit = "username"` |

These variables have to be in the `[social]` table of `config.toml` or its equivalent for `YAML` or `JSON`.
```toml
[social]
	github = "UtkarshVerma"
```

Once this is done, write up the "**About Me**" section of your website in Markdown as directed here:[Error and About Pages](https://github.com/UtkarshVerma/hugo-dream-plus#error-and-about-pages).

### Toggling the views
As stated earlier, this theme has two views, **Card view** and **Post view**. To define your desired view, modify the `contentType` variable in `params` in the config file as follows:
```toml
contentType = "cards"    #Enables the card view.
contentType = "posts"    #Enables the post view.
```

One clear distinction between both the view is that **Card** view doesn't support posts, instead it redirects to the specified link, while **Post** view does.
You may test them out yourselves by visiting my sites(stated above) which use them.
Also, post/card creation is done differently for both the views. It is as follows:
```shell
hugo new cards/example.md		#Card creation
hugo new posts/example.md		#Post creation
```

After this, just open your MarkDown card/post and provide the parameters for the card/post.

### Image background
To enable setting images as background, you'll have to disable **random colour background** first by setting `enableColorBG` to false.
Also, enabling image background feature requires the modification of two variables, namely `bgImage` and `bgList`. If you prefer a single image background, then simply set the value of `bgImage` as the absolute path of your image. For example,
```
bgImage = "/images/bg1.jpeg"
```
You can also enable random background feature which switches the background between a provided images list(stored in `bgList`), every time the site is reloaded. For example,
```
bgList = ["/images/bg1.jpeg", "/images/bg2.jpeg", "/images/bg3.jpeg"]
```
You may also add blurring effect to the background image using `bgBlur`.

### Device detection
You may configure your website based on the client device by using the `isMobile` JS variable. It is `true` when the client device is a mobile and vice versa.

### Error and About pages
This theme supports total customization of **about** and **error** pages. These pages may be customized through the [`about.md`](/exampleSite/content/about.md) and [`404.md`](/exampleSite/content/404.md) files. Once finished customizing, copy them in the `/content` directory of your Hugo site.

### Custom favicon
You may also set a custom favicon for your website using the `favicon` config variable. For example,
```
favicon = "/images/defaultFav.ico"
```

### Shorte.st website script
The [Shorte.st](https://shorte.st) website script has been implemented in this theme. To use it, you'll first have to enable this feature by setting `enableShortest` to `true` and then setting the **API Token** you got from Shorte.st to `shortestToken`, and after that, define your domains as a list in the `shortestDomains` config variable.

### Some other configurations
There are some other minor configurations as well. You may set them up by referring to the comments inside the config file.

## Documentation
The documentation for this repository is currently under work and is added to this repository's [wiki](https://github.com/UtkarshVerma/hugo-dream-plus/wiki).
Wiki contributions are most welcome. Feel free to ask me about this theme's features for that.

## Nearly Finished
After finishing the configurations, you're good to go. So, test your website using:
```bash
hugo server
```
Your site should now be locally available at [http://localhost:1313](http://localhost:1313) for testing purposes.

For testing the example site, you'll have to explicitly specify the config file to Hugo. This is done as follows:
```bash
#For post view demo
hugo --config posts.toml server

#For card view demo
hugo --config cards.toml server
```

## Contributing
Found something interesting to add to this theme or rather a :beetle:bug? Let me know about it through the [issue tracker](https://github.com/UtkarshVerma/hugo-dream-plus/issues). [Pull requests](https://github.com/UtkarshVerma/hugo-dream-plus/pulls) are also welcome.
For more detailed instructions on how to contribute, refer to [**CONTRIBUTING.md**](/CONTRIBUTING.md)

## License
This theme is released under the [**MIT**](/LICENSE) license.

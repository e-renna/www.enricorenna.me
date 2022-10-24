---
title: "How I Easily Deployed My Own Website"
date: 2022-10-24T14:00:00+01:00
categories: [Homelab, Website]
draft: false
---


In my free time, I love to work on personal projects (such as my homelab) and solve CTFs challenges. I figured out that it would be great if I could document all my attempts and experiments. I also wanted to share all of this, so that my experiences could help someone else in their project. As an added this would help me improve my reporting skills.

The conclusion was, I needed a personal website in which I could share anything I wanted, without the limitations that some of the already available big platforms impose. Ideally, the framework would be free, open source, and easy to customise. Being able to publish it through GitHub pages would have been an added benefit. This would cut maintenance costs and the need to set up a VPS that would need to be updated regularly.

From a cybersecurity point of view, the smaller the attack surface, the better. Solutions like Ghost or WordPress, are easier to use once deployed as they provide nice editors with an easy-to-use admin panel. However, the attack surface and maintenance costs are higher compared to a static website. That is the main reason why I opted for [Hugo](https://gohugo.io/).

Hugo claims to be the world's fastest framework for building websites. It is not a CMS but a static site generator. It is indeed very fast, customisable and once all the mechanics have been understood also easy to use.

Currently, Hugo has a total of 63,000 stars on [GitHub](https://github.com/gohugoio/hugo). This might help you understand how popular this project is. Considering it is also open source, it is really unlikely this project could die anytime soon. This is the power of open-source projects after all!

## Getting started with Hugo

Whatever OS you have installed on your machine, you will most likely be able to use Hugo, as they provide support for the following systems:

- macOS (Darwin) for x64, i386, and ARM architectures
- Windows
- Linux
- OpenBSD
- FreeBSD

I am using an Arch-based Linux distro, and therefore I will easily install Hugo through my packet manager. However, if you are using another OS, simply follow [their official tutorial here.](https://gohugo.io/getting-started/installing)

Once you are done installing Hugo, open your terminal and use the command 'hugo version' to verify that the installation was successful. You should get an output similar to this:
```txt
hugo version
hugo v0.104.3+extended linux/amd64 BuildDate=unknown
```
If you get an error of any kind, make sure that you've followed all the installation steps correctly.

## Creating a new Site

Creating a new site with Hugo is extremely easy. On your terminal move to a suitable directory. Hugo will create a new folder there with all your website files.
Once you are in the right directory, run the following command `hugo new site SITENAME`, and replace SITENAME with the name of your choice. Here is an example:
```txt
hugo new site tutorial

Congratulations! Your new Hugo site is created in /home/.../Hugo/tutorial.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
Choose a theme from https://themes.gohugo.io/ or
create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

## Adding a Theme to your New Site

What makes Hugo amazing is not just the framework itself, but the community that surrounds it! There are thousands of themes freely available to you, and installing them is extremely easy! Go [here](https://themes.gohugo.io/), and pick a theme you like. Then click on the Download button that you can find on the theme page. In my case, this will be [PaperMod](https://themes.gohugo.io/themes/hugo-papermod/). The download button will most likely redirect you to a GitHub page in which you will find a guide on how to install the theme. If you wish to install PaperMod you can follow these steps and enter these commands in your terminal:

```
cd tutorial # Move to the website folder

git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```
You've now successfully downloaded the PaperMod theme and installed it in your themes folder. However, you still have to tell Hugo to use this theme for your website.
To do so, open the `config.toml` and add this string at the end of the file: `theme = 'PaperMod'`.
If you wish to use a single command instead of opening and editing the file you can use the following:
```
echo "theme = 'PaperMod'" >> config.toml
```
This command will append the string `theme = 'PaperMod'` to the config file.
If you want to customise your theme to fit your liking, just read the documentation on the GitHub repository of your theme.

## Creating your first Article/Page

You will now want to create your first article or a page with some information. Luckily for you, creating a page is extremely easy, all it takes is a single command:
```txt
hugo new posts/new-page.md
```

You can find the newly created page in the contents/posts folder. By opening it you should see something similar to this:
```txt
---
title: "New Page"
date: 2022-10-15T13:53:18+01:00
draft: true
---
```

This is the settings of the page itself. You can change the page title, the date and whether the page should be displayed on the website or not by changing draft to false.
Then under the `---` you can start writing the page content. Hugo uses MarkDown. If you are not familiar with it, you can find a helpful [cheatsheet here](https://www.markdownguide.org/cheat-sheet/).


## Website Preview

Hugo offers a live server that can render your website. It will refresh every time you modify any file inside your website directory so that you can preview the edits live. To benefit from this feature, all you have to do is to start the server. First, move to the main directory of your Hugo site, and then enter this command on your terminal:
```txt
hugo server -D
```
Now, go to http://localhost:1313 and you will be able to see a preview of your website!

## Building the site

Once you are satisfied with your edits, and you are ready to publish your site, all you need to do is build the site, so that you have all the files you need to upload on your hosting or push to your GitHub Repository. The following command will build the site:
```txt
hugo -D
```
It should take less than a second for Hugo to build the site, once done you can open the `public` folder, which can be found inside your Hugo site directory.
There you will find all the files you need to finally deploy your website.

## Conclusion

I've personally created a [GitHub Repository](https://github.com/e-renna/www.enricorenna.me) dedicated to this very site. There you will be able to see all the config files and the built website as well. I've then ended up using GitHub Pages to host the site, as it is very easy to use, and can be connected to a custom domain. If you are interested in understanding how GitHub Pages work, and how you can host your website there are well, I'd suggest you open [this page](https://pages.github.com/), where you can find all the information you are looking for.

Good luck deploying your newly made website!

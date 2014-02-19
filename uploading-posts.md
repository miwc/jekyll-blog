# Uploading blog posts using Jekyll

## Useful documentation

Jekyll basically talks us through everything in their documentation: <http://jekyllrb.com/docs/>

As a starting point, clone the repository: https://github.com/miwc/miwc.github.io

You can work from the IDE or locally; unless you have Windows, in which case don't even think about it...

## Steps

### Step 1

Ben made our lives easier by adding a Gemfile, you just need to install it in the right directory.

### Step 2

You'll need to be on the source branch. Mine was already there, but to make sure run `git checkout source`.

### Step 3

In the `_posts` directory, add a new file for your article. The naming convention is quite important but everything is explained in Jekyll's documentation on posts.

Or you could cheat and copy the structure of the existing file names like I did. It should be something like:

  ```
  YYYY-MM-DD-give-me-a-title.md
  ```
  
where .md means it's written in Markdown.

### Step 4

The easiest way to figure out how to structure a file is to look at one of our previous posts, but again the Jekyll docs are awesome. At the top of the file you need to chuck in some parameters, including layout, title, date and biofooter. Our typical "Front-matter", as Jekyll calls it, is:

  ```
  ---
  layout : post
  title: "Give Me a Title"
  date: YYYY-M-D HH:MM:SS
  categories: ruby learning teaching coding etc
  biofooter: false
  ---
  ```

**Tip:** If you want to upload the post but not publish it yet, you can add a parameter saying:

  ```
  published: false
  ```
  
Underneath this you can add your blog post (written in Markdown). Again, all of the formatting stuff like how to include links and pictures of kittens and things is explained in the Jekyll docs.

### Step 5

Before deploying your blog post to the interwebs, you should probably check it locally to make sure it all looks OK and the links work and such. The command you want is:

  ```
  bundle exec jekyll serve --p YOUR_PORT --watch
  ```

**Hint:** You want to be in the `miwc.github.io` directory.

The `--p YOUR_PORT` bit is there so you can specify your port number, which is the same as your normal IDE one, and then view the page at http://yourusername.ide.makeitwithcode.com:YOUR_PORT

Make sure you stop the server when you're done.

### Step 6

Assuming the new blog post appears and looks beautiful, you're ready to deploy! Run:

  ```
  bundle exec rake jekyll:publish
  ```
  
You'll need to enter your GitHub creds, and then it'll be live on the MIWC blog! Unless you said `published: false`, in which case it definitely shouldn't be live yet...

### Step 7

Finally, you need to update the GitHub repository. Despite the fact that it's on the website, the source branch won't have been updated and that's bound to cause problems at some point...

You'll need to use a set of Git commands:

  ```
  git add my_blog_post
  git commit -m "uploading my awesome blog post"
  git push origin source
  ```
  
And you're done!

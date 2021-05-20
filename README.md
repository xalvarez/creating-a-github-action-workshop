# Creating a GitHub Action Workshop

This repository contains the slides for my "Creating a GitHub Action" workshop.

If you want to see an example of a simple GitHub Action see: [prevent-file-change-action][1]

## Viewing the slides

You can either view the slides using docker:

```bash
docker run --rm -p 1948:1948 -v $PWD/slides:/slides webpronl/reveal-md:5.1.0

# Slides will be available under http://localhost:1948/slides.md
```

Or npm:

```bash
npm i
npm start

# Slides will be available under http://localhost:1948
```

### Watching for changes

You can also modify the slides and view the changes without
having to restart the application as follows:

**Docker**
```bash
docker run --rm -p 1948:1948 -p 35729:35729 -v $PWD/slides:/slides webpronl/reveal-md:5.1.0 /slides -w
```

**npm**
```bash
npm run watch
```

[1]: https://github.com/marketplace/actions/prevent-file-change

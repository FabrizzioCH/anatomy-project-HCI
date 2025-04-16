<div align="center">
  <img alt="Astro Citrus logo" src="https://github.com/ArtemKutsan/astro-citrus/blob/main/src/assets/images/logo.svg" width="70" />
</div>
<h1 align="center">
  Astro Citrus
</h1>

Astro Citrus is a simple opinionated starter built with the Astro framework. Use it to create an easy-to-use blog or website.

## Table Of Contents

1. [Key Features](#key-features)
2. [Demo](#demo)
3. [Quick start](#quick-start)
4. [Preview](#preview)
5. [Commands](#commands)
6. [Configure](#configure)
7. [Updating](#updating)
8. [Adding posts and notes](#adding-posts-and-notes)
   - [Post Frontmatter](#post-frontmatter)
   - [Note Frontmatter](#note-frontmatter)
   - [Frontmatter Snippet](#frontmatter-snippet)
9. [Pagefind search](#pagefind-search)
10. [Analytics](#analytics)
11. [Deploy](#deploy)
12. [Acknowledgment](#acknowledgment)

## Key Features

- Astro v5 Fast 🚀
- TailwindCSS Utility classes
- Accessible, semantic HTML markup
- Responsive & SEO-friendly
- Dark / Light mode, using Tailwind and CSS variables
- MD & [MDX](https://docs.astro.build/en/guides/markdown-content/#mdx-only-features) posts & notes
  - Includes [Admonitions](http://astrocitrus.artemkutsan.pp.ua/posts/markdown-elements/admonistions/)
- [Satori](https://github.com/vercel/satori) for creating open graph png images
- [Automatic RSS feed](https://docs.astro.build/en/guides/rss)
- [Webmentions](https://webmention.io/)
- Auto-generated:
  - [sitemap](https://docs.astro.build/en/guides/integrations-guide/sitemap/)
  - [robots.txt](https://github.com/alextim/astro-lib/blob/main/packages/astro-robots-txt/README.md)
  - [web app manifest](https://github.com/alextim/astro-lib/blob/main/packages/astro-webmanifest/README.md)
- [Pagefind](https://pagefind.app/) static search library integration
- [Astro Icon](https://github.com/natemoo-re/astro-icon) svg icon component
- [Rehype Pretty Code](https://rehype-pretty.pages.dev/) code blocks and syntax highlighter

## Demo

Check out the [Demo](https://astrocitrus.netlify.app/)

## Quick start

[Create a new repo](https://github.com/artemkutsan/astro-citrus/generate) from this template.

```bash
# npm 7+
npm create astro@latest -- --template artemkutsan/astro-citrus

# pnpm
pnpm dlx create-astro --template artemkutsan/astro-citrus
```

[![Deploy with Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/artemkutsan/astro-citrus) [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fartemkutsan%2Fastro-citrus&project-name=astro-citrus)

## Preview

| ![Light Theme 01](https://github.com/ArtemKutsan/astro-citrus/blob/main/public/images/screenshot01.png?raw=true) | ![Light Theme 02](https://github.com/ArtemKutsan/astro-citrus/blob/main/public/images/screenshot02.png?raw=true) |
|-------------|-------------|
| ![Dark Theme 03](https://github.com/ArtemKutsan/astro-citrus/blob/main/public/images/screenshot03.png?raw=true) | ![Light Theme 04](https://github.com/ArtemKutsan/astro-citrus/blob/main/public/images/screenshot04.png?raw=true) |
| ![Light Theme 05](https://github.com/ArtemKutsan/astro-citrus/blob/main/public/images/screenshot05.png?raw=true) | ![Light Theme 06](https://github.com/ArtemKutsan/astro-citrus/blob/main/public/images/screenshot06.png?raw=true) |
| ![Dark Theme 07](https://github.com/ArtemKutsan/astro-citrus/blob/main/public/images/screenshot07.png?raw=true) | ![Dark Theme 08](https://github.com/ArtemKutsan/astro-citrus/blob/main/public/images/screenshot08.png?raw=true) |

## Commands

Replace pnpm with your choice of npm / yarn

| Command          | Action                                                         |
| :--------------- | :------------------------------------------------------------- |
| `pnpm install`   | Installs dependencies                                          |
| `pnpm dev`       | Starts local dev server at `localhost:3000`                    |
| `pnpm build`     | Build your production site to `./dist/`                        |
| `pnpm postbuild` | Pagefind script to build the static search of your blog posts  |
| `pnpm preview`   | Preview your build locally, before deploying                   |
| `pnpm sync`      | Generate types based on your config in `src/content/config.ts` |

## Configurar

- Edita el archivo de configuración `src/site.config.ts` para los metadatos básicos del sitio.
- Actualiza el archivo `astro.config.ts`:
  - **Importante**: la propiedad `site` con tu propio dominio.
  - [Opciones de astro-webmanifest](https://github.com/alextim/astro-lib/blob/main/packages/astro-webmanifest/README.md)
- Reemplaza y actualiza los archivos dentro de la carpeta `/public`:
  - `icon.svg`: usado como fuente para crear favicons e íconos del manifiesto.
  - `social-card.png`: usado como la imagen predeterminada para `og:image`.
- Modifica el archivo `src/styles/global.css` con tus propios estilos para los modos claro y oscuro.
  - También puedes modificar los temas para los bloques de código Markdown generados por [Rehype Pretty Code](https://rehype-pretty.pages.dev/). Astro Citrus incluye un tema oscuro (rose-pine) y uno claro (rose-pine-dawn), que se encuentran en `src/site.config.ts`. Puedes encontrar más temas y opciones [aquí](https://shiki.matsu.io/).
- Edita los enlaces sociales en `src/components/SocialList.astro` para agregar/reemplazar tu perfil de redes sociales. Los íconos se pueden encontrar en [icones.js.org](https://icones.js.org/), según las instrucciones de [Astro Icon](https://www.astroicon.dev/guides/customization/#find-an-icon-set).
- Crea/edita publicaciones y notas para tu blog dentro de `src/content/post/` y `src/content/note/` con archivos `.md` o `.mdx`. Consulta [más abajo](#adding-posts-and-notes) para más detalles.
  - Lee [esta publicación](http://astrocitrus.artemkutsan.pp.ua/posts/webmentions/) para agregar webmentions a tu sitio.
- Imagen OG:
  - Si deseas cambiar el estilo de la imagen generada por la biblioteca Satori, abre `src/pages/og-image/[slug].png.ts` y edita la función `markup` donde puedes modificar el HTML y las clases de Tailwind según sea necesario. Puedes usar este [playground](https://og-playground.vercel.app/) para ayudarte con el diseño.
  - También puedes crear tus propias imágenes OG y omitir que Satori las genere automáticamente agregando una propiedad `ogImage` en el frontmatter con un enlace al recurso. Un ejemplo se encuentra en `src/content/post/social-image.md`. Más información sobre frontmatter [aquí](#frontmatter).
- Opcional:
  - Fuentes: Este tema establece el elemento `body` con la familia de fuentes `font-mono`, ubicada en el archivo CSS global `src/styles/global.css`. Puedes cambiar las fuentes eliminando la variante `font-mono`, tras lo cual TailwindCSS usará por defecto la pila de fuentes `font-sans` [documentada aquí](https://tailwindcss.com/docs/font-family).

## Updating

If you've forked the template, you can [sync the fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork) with your own project, remembering to **not** click Discard Changes as you will lose your own.

If you have a template repository, you can add this template as a remote, as discussed [here](https://stackoverflow.com/questions/56577184/github-pull-changes-from-a-template-repository).

## Adding posts and notes

This theme utilises [Content Collections](https://docs.astro.build/en/guides/content-collections/) to organise local Markdown and MDX files, as well as type-checking frontmatter with a schema -> `src/content/config.ts`.

Adding a post/note is as simple as adding your .md(x) files to the `src/content/post` and/or `src/content/note` folder, the filename of which will be used as the slug/url. The posts included with this template are there as an example of how to structure your frontmatter. Additionally, the [Astro docs](https://docs.astro.build/en/guides/markdown-content/) has a detailed section on markdown pages.

### Post Frontmatter

| Property (\* required) | Description |
|------------------------|-------------|
| **title \***          | Self-explanatory. Used as the text link to the post, the h1 on the post's page, and the page's title property. Has a max length of 60 chars, set in `src/content/config.ts`. |
| **description \***    | Similar to above, used as the SEO description property. Has a min length of 50 and a max length of 160 chars, set in the post schema. |
| **publishDate \***    | Again, pretty simple. To change the date format/locale, currently **en-GB**, update the date option in `src/site.config.ts`. Note you can also pass additional options to the `<FormattedDate>` component if required. |
| **updatedDate**       | This is an optional date representing when a post has been updated, in the same format as the `publishDate`. |
| **seriesId**          | An optional property that groups posts into a series. Posts with the same `seriesId` are considered part of the same series and can be displayed together in order. This allows for better organization of related content. |
| **orderInSeries**     | A numeric value defining the position of a post within a series. Lower values indicate earlier posts in the series, while higher values appear later. Used for sorting and navigation between posts within the same series. |
| **tags**             | Tags are optional with any created post. Any new tag(s) will be shown in `yourdomain.com/posts` & `yourdomain.com/tags`, and generate the page(s) `yourdomain.com/tags/[yourTag]`. |
| **coverImage**       | This is an optional object that will add a cover image to the top of a post. Include both `src`: "_path-to-image_" and `alt`: "_image alt_". You can view an example in `src/content/post/cover-image.md`. |
| **ogImage**          | This is an optional property. An OG Image will be generated automatically for every post where this property **isn't** provided. If you would like to create your own for a specific post, include this property and a link to your image, the theme will then skip automatically generating one. |
| **draft**            | This is an optional property as it is set to `false` by default in the schema. By setting it to `true`, the post will be filtered out of the production build in a number of places, including `getAllPosts()` calls, OG images, RSS feeds, and generated page[s]. You can view an example in `src/content/post/draft-post.md`. |


### Note Frontmatter

| Property (\* required) | Description                                        |
| ---------------------- | -------------------------------------------------- |
| title \*               | string, max length 60 chars.                       |
| description            | to be used for the head meta description property. |
| publishDate \*         | ISO 8601 format with offsets allowed.              |

### Frontmatter snippet

Astro Citrus includes a helpful VSCode snippet which creates a frontmatter 'stub' for posts and note's, found here -> `.vscode/post.code-snippets`. Start typing the word `frontmatter` on your newly created .md(x) file to trigger it. Visual Studio Code snippets appear in IntelliSense via (⌃Space) on mac, (Ctrl+Space) on windows.

## Pagefind search

This integration brings a static search feature for searching blog posts and notes. In its current form, pagefind only works once the site has been built. This theme adds a postbuild script that should be run after Astro has built the site. You can preview locally by running both build && postbuild.

Search results only includes pages from posts and notes. If you would like to include other/all your pages, remove/re-locate the attribute `data-pagefind-body` to the article tag found in `src/layouts/BlogPost.astro` and `src/components/note/Note.astro`.

It also allows you to filter posts by tags added in the frontmatter of blog posts. If you would rather remove this, remove the data attribute `data-pagefind-filter="tag"` from the link in `src/components/blog/Masthead.astro`.

If you would rather not include this integration, simply remove the component `src/components/Search.astro`, and uninstall both `@pagefind/default-ui` & `pagefind` from package.json. You will also need to remove the postbuild script from here as well.

You can reduce the initial css payload of your css, as demonstrated [here](https://github.com/artemkutsan/astro-citrus/pull/145#issue-1943779868), by lazy loading the web components styles.

## Analytics

You may want to track the number of visitors you receive to your blog/website in order to understand trends and popular posts/pages you've created. There are a number of providers out there one could use, including web hosts such as [vercel](https://vercel.com/analytics), [netlify](https://www.netlify.com/products/analytics/), and [cloudflare](https://www.cloudflare.com/web-analytics/).

This theme/template doesn't include a specific solution due to there being a number of use cases and/or options which some people may or may not use.

You may be asked to included a snippet inside the **HEAD** tag of your website when setting it up, which can be found in `src/layouts/Base.astro`. Alternatively, you can add the snippet in `src/components/BaseHead.astro`.

## Deploy

[Astro docs](https://docs.astro.build/en/guides/deploy/) has a great section and breakdown of how to deploy your own Astro site on various platforms and their idiosyncrasies.

By default the site will be built (see [Commands](#commands) section above) to a `/dist` directory.

## Acknowledgment

**This theme was inspired by [Astro Theme Cactus](https://github.com/chrismwilliams/astro-theme-cactus) by [Chriss Williams](https://github.com/chrismwilliams). Huge thanks to Chriss for his amazing work and inspiration!** 🚀👏

## License

MIT

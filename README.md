# The Handbook for Innovative Design's Web Tier
By [Christian Le](https://github.com/cle1994) for
[Innovative Design](http://innovativedesign.club/)

# Table of Contents

* [Preface](#preface)
* [Acknowledgements](#acknowledgements)
* [What is Web Tier?](0-what_is_web_tier.md)
* [Setup and Basics](1-setup_and_basics.md)
    * [Git](1-setup_and_basics.md#git)
      * [GitHub](1-setup_and_basics.md#github)
      * [Installation](1-setup_and_basics.md#git-installation)
    * [Node](1-setup_and_basics.md#node)
      * [Installation](1-setup_and_basics.md#node-installation)
    * [Things you might find useful](1-setup_and_basics.md#helpful-things)
      * [Sublime](1-setup_and_basics.md#helpful-sublime)
      * [Atom](1-setup_and_basics.md#helpful-atom)
      * [Vim](1-setup_and_basics.md#helpful-vim)
* [Resources](2-resources.md)
* [HTML](3-html.md)
  * [Elements](3-html.md#elements)
  * [Tags](3-html.md#tags)
    * [Head/Body](3-html.md#tags-head)
    * [Meta](3-html.md#tags-meta)
    * [Link](3-html.md#tags-link)
    * [Script](3-html.md#tags-script)
    * [Many, many more...](3-html.md#tags-rest)
  * [Attributes](3-html.md#attributes)
  * [Example](3-html.md#example)
* [CSS](4-css.md)
  * [Selectors](4-css.md#selectors)
  * [Media Queries](4-css.md#media-queries)
  * [Before/After](4-css.md#before)
  * [Animations/Key-frames](4-css.md#animations)
  * [Prefixing](4-css.md#prefixing)
  * [Examples](4-css.md#examples)
* [SCSS](5-scss.md)
  * [Compiled](5-scss.md#compiled)
  * [Nesting](5-scss.md#nesting)
  * [Variables](5-scss.md#variables)
  * [Mixins](5-scss.md#mixins)
  * [Extending](5-scss.md#extending)
  * [Import](5-scss.md#import)
* [Javascript](6-javascript.md)

<a name="preface"></a>
# Preface
**This is by no means the definitive guide to all things web or web
development.**

Whether you're in Web Exploration or Web Development, it doesn't matter, you're
here to both learn and teach. You'll learn from your tier leaders and they from
you, it's two way relationship. And as cliche as this sounds, you get what you
put in. If you want to learn a lot, put yourself out there.


I wrote this as a guide to aid in your growth as a web developer, whether your
focus is in development or in design. I also wanted a basis for all web tiers
going forward to have. Take this book, learn, teach, grow, and then make pull
requests for all the dumb things I write or all the mistakes I make. But let's
face it I don't make mistakes - just kidding, maybe.

The information found in this book comes from my failures, errors, and growth as
an intern and a technical co-founder. Again, this isn't a definitive guide to
anything, just an aid, take it how you will.

Also, I use a Mac, so instructions will be assuming you use a Mac, sorry
:disappointed:. I'll try to add as much Windows and Linux as a can but no
guarantees it'll work. (Please pull request me for added instructions for those
operation systems).

**Author's Blurb**

And by now you're probably asking, *who the hell is this guy*. Well, I'm a long
time InnoD member, officer, advisor, and senior executive advisor (it's not a
real thing). I was a member of photo tier my first semester in InnoD. The
following semester I joined as VP of Photo Services and Recollections and lead
photo tier. I then went on to lead web tier the semester after, before there was
a web exploration. After that, I started and lead the first web exploration
tier. Then I moved away from web and led photo tier and product tier during
my last semester at Berkeley. I've been here awhile as you can see. I like to
think I made great impact (for better or for worse) being a part of Innovative
Design but I'll let others judge that.

More on my experiences with web dev, I worked largely in Angular.js
as I started learning web development. I was one of four engineers at
[Storefront](http://thestorefront.com) my sophomore year working on the
Angular app with some Ruby of Rails. I then moved to working a lot in Node.js
(server side stuff) during my free time and building out full stack web
apps. During my junior year at Berkeley, I co-founded
[Outcomes.com](https://outcomes.com). In the first 7 months, we bootstrapped a
health tech company and started a pilot with Alameda Health System. If you're
interested, the entire platform is built in Angular, React, and Node. As of
recent, I've moved to building almost all projects with React and Node. The
rewrite of [my personal website](http://christianle.com) for example. I'm
currently exploring Angular 2.0 and Elm as possibilities for future projects.

<a name="acknowledgements"></a>
# Acknowledgements
Just wanted to say thank you to those that helped me as I wrote this.

[Julia Sun](https://github.com/jubearsun) - For editing my terrible writing

Check out her website [here](http://juliasun.io).

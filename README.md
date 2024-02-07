This is the repo that backs [BYU's Scientific Computing Course](https://byuhpc.github.io/sci-comp-course/), which is generated by GitHub Pages.

To pull and run the website locally:

```bash
git clone git@github.com:BYUHPC/sci-comp-course.git
cd sci-comp-course
# I had to do the following to avoid permissions issues, not sure if that's a setup problem on my end
export GEM_HOME="$(ruby -e 'puts Gem.user_dir')"
export GEM_PATH="$GEM_HOME"
# Install the Ruby crap and run
bundle install
bundle exec jekyll serve
```



## Enhancements

Adding `?for_iframe=true` to the URL for a page on this site will add `target="_top"` to each link on said page and hide the header and footer, allowing it to be used in a iframe with less wonkiness. This should allow smoother integration with Canvas once I get around to it.

"Shell and Slurm Practice" is meh; it'd be nice to have a `find` thrown in there (plus material on `find`), and make it more open-ended and amenable to combining sed/grep/awk.

Our [Linux tutorial](https://rc.byu.edu/documentation/unix-tutorial/) could be basically a drop-in replacement for a lot of lesson 2.

The website situation is stupid--Canvas has nice navigation stuff, but it can't really be used for code samples because doing syntax highlighting manually is insane. Gordon Bean has a kind-of solution that allows you to use Markdown in Canvas, but it's not as nice as this way. He's working on something that will build a Canvas course from a Git repo which would be sweet but it sounds like that's a ways off. **Update**: we're probably going to move readings and assignments to a knowledge base-type wiki, then use iframes to embed them in Canvas; this will mean adding `target="_blank"` to all the hrefs so that they don't just open within the iframe.

I need to re-make some of the videos with the current example code; the ones that are especially important:

- Optimization
- MPI

Once LLVM or GCC supports compiling DPC++ for GPUs, use that rather than `nvc++` for the GPU phase. Looks like [AdaptiveCpp](https://github.com/AdaptiveCpp/AdaptiveCpp) might be a good option since it can compile for AMD GPUs as well.

Updating to C++23 will be nice, especially since we'll finally get `std::mdspan`. Once compilers finally [support modules](https://en.cppreference.com/w/cpp/compiler_support/20), all the code should probably be updated to use them since they're nicer than headers.

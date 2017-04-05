# Installing Ruby

IT may have already set up Ruby on your machine. Follow the steps below to verify that an acceptable version of Ruby is available. 

1. Check by going to terminal and typing:

   ```
   $ ruby -v
   ```
2. If below Version 2.2.2 you will want to upgrade ruby.

   ```
   $ brew upgrade
   $ brew install rbenv
   $ brew install ruby-build
   $ rbenv install 2.2.2
   ```

3. Add this line to your `.bash_profile` so that rbenv works correctly:

   ```sh
   eval "$(rbenv init -)"
   ```

4. Open a new Terminal tab/window, or reload your `.bash_profile`:

   ```
   source ~/.bash_profile
   ```

5. Use rbenv to switch to the Ruby version you just installed:

   ```
   $ rbenv global 2.2.2
   $ rbenv shell 2.2.2
   ```

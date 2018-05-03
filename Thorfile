require 'date'
require 'colorize'

class Default < Thor

  no_commands do

    def post_name(path)
      return File.basename(path).split("-").drop(3).join("-")
    end

    def combine(path, name)
      return File.dirname(path) + "/" + name
    end

    def dateify(name)
      return Date.today().to_s() + "-" + name
    end

  end

  
  desc 'serve', 'Serves the blog locally through Jekyll\'s embedded server'
  def serve
    exec("jekyll serve")
  end

  desc 'build', 'Builds the static site'
  def build
    exec("jekyll build")
  end

  desc 'new SLUG', 'Creates a new post with the provided slug'
  def new(slug)
    datename = dateify(slug)
    filename = "_posts/#{datename}.md"
    File.new(filename, "w")
    puts("Created file: ".green + "#{filename}".yellow)
  end
  
  desc 'refresh PATH', 'Updates a given file path to match current date'
  def refresh(path)
    newpath = combine(path, dateify(post_name(path)))
    File.rename(path, newpath)
    puts("Refreshed file: #{newpath.yellow}")
  end

end


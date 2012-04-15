fs      = require 'fs'
{exec}  = require 'child_process'
util    = require 'util'



coffeeDir = 'src/'


task 'build', 'Build a single JavaScript file from prod files', ->
  util.log "Building..."
  exec "coffee --join src/app.js --compile src/Models/*.coffee src/Collections/*.coffee src/Views/*.coffee  src/main.coffee", (err, stdout, stderr) ->
    if err
      util.log err
      exec 'growlnotify Coffee ERROR -m "Could not build js"'  
    util.log stdout if stdout
    exec 'growlnotify Coffee -m "Built js"' unless err
  

task 'buildCss', 'Building a single css file out of all less files', ->
  util.log "lessing.."
  exec "lessc css/style.less > css/style.css -x", (err, stdout, stderr) ->
    if err
      util.log err 
      exec 'growlnotify Less ERROR -m "Could not build css"'
    util.log stdout if stdout
    exec 'growlnotify Less -m "Built css"' unless err
    

#src/Collections/*.coffee src/Views/*.coffee 

task 'watch', 'Watch prod source files and build changes', ->
    util.log "Watching for changes in #{coffeeDir}"
    exec "find src -name *.coffee", (err, stdout, stderr) ->
      ls = stdout.split("\n").reverse()
      ls.shift()
      for file in ls then do (file) ->
          util.log "Adding watcher for file #{file}"
          #util.log file[1]
          fs.watchFile file, (curr, prev) ->
              if +curr.mtime isnt +prev.mtime
                  util.log "Saw a change!"
                  invoke 'build'
      util.log "Watching for changes in the less file"
      fs.watchFile 'css/style.less', (curr, prev) ->
        if +curr.mtime isnt +prev.mtime
          util.log "Saw a change!"
          invoke 'buildCss'
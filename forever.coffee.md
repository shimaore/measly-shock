    forever = require 'forever-monitor'
    pkg = require './package.json'

    child = (new forever.Monitor) 'server.coffee.md',
      silent: true
      options: []
      command: 'coffee'

    child.on 'exit', "#{pkg.name} has exited"

    child.start()

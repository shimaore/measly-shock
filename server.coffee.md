Provides a service to reload opensip routes.
This is meant to be used with `abstracted-birds` since the current ccnq3 opensips package doesn't use the AMQP bus.

    ccnq3 = require 'ccnq3'


    config = null
    ccnq3.config (c) -> config = c

    ccnq3.command.handler (req,cb) ->
      if req.opensips is 'dr_reload'
        command = ccnq3.opensips.command 'dr_reload'
        ccnq3.opensips.mi config.opensips.mi_port ? 30000, command, (e,msg) ->
          throw e if e
          cb ccnq3.opensips.parse msg

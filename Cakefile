remote = 'iu:../dev/ben/diageo/wclass'

fs 					= require 'fs'
{exec} 				= require 'child_process'

ansi =
	red  			: '\x1B[31m'
	green 			: '\x1B[36m'
	yellow 			: '\x1B[33m'
	blue  			: '\x1B[34m'
	dark_grey  		: '\x1B[1;30m'
	light_grey  	: '\x1B[1;32m'
	reset   		: '\x1B[0m'

log = (message, color) ->
	console.log ansi[color] + message + ansi.reset

option '-m', '--message [COMMIT_MESSAGE]', 'set git commit message'

task 'build', 'build app from src files', (options) ->
	invoke 'build:jade'

task 'build:stylus', 'build style.css from src/styl', ->
	exec 'stylus -c -u nib -o www/css src/stylus/style.styl', (err, stdout, stderr) ->
		err && throw err
		log 'Build Stylus OK!', 'green'
		invoke 'build:jade'

task 'build:jade', 'build index.html from src/jade', ->
	exec 'jade src/jade/ --out ./', (err, stdout, stderr) ->
		err && throw err
		log 'Build Jade OK!', 'green'


B=node_modules/.bin
O=src/main/resources/www/steam

default: 
	$B/gulp

clean:
	$B/gulp clean

watch:
	$B/gulp watch

check:

launch:
	java -Dwebdev=1 -Xmx4g -jar ../h2o-app/build/libs/h2o-app.jar

unit-test:
	$B/gulp build-test-script && node $O/js/steam-tests.js -u | $B/faucet 

test-raw:
	$B/gulp build-test-script && node $O/js/steam-tests.js -s

test:
	$B/gulp build-test-script && node $O/js/steam-tests.js -s | $B/faucet

coverage:
	@mkdir -p $O/coverage
	$B/gulp build-test-script && $B/istanbul cover --dir $O/coverage -x "**/lib/**" $O/js/steam-tests.js && $B/istanbul report --dir $O/coverage cobertura

doc:
	$B/coffee help.coffee

refresh:
	$B/coffee help.coffee --host=localhost:54321

.PHONY: default watch clean unit-test test-raw test coverage launch 


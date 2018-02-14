
<!doctype>

<!--
Zak Clough
Pokemon Clicker
4/20/2015
-->

<!--
Code for later on.
<span style="color:blue;">&male;</span>
<span style="color:red;">&female;</span>
-->


<html ng-app="pokemonClickerApp">

	<head>
		<link rel="stylesheet" type="text/css" href="interface.css" />
		<title>Pokemon Clicker</title>
		<script>
  			(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  			(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  			m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  			})(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  			ga('create', 'UA-76521632-1', 'auto');
  			ga('send', 'pageview');

		</script>
	</head>

	<body ng-controller="PokemonClickerCtrl">
        <div id="header">
		<h1>Pokemon Clicker</h1>
        <h2><strong>Update Coming Soon!</strong></h2>
		<h3>Instructions: Click the yellow Sitrus Berry to get berries.</h3>
		<h3>Then use those berries to buy pokemon by clicking on their picture.</h3>
        </div>
	    <div><img src="Images/pokeball.png" id="pokeballBar"></div>
        <div id="main">
            <br />
		<img src="Images/sitrus_berry.png" ng-click="berryClick()">
	<br /><br /><br />
		<table>               <!-- Sitrus Berries -->
			<tr ng-repeat="(berryName, berry) in gameData.berries">
				<td>{{berry.count}} {{berryName | capitalize}}
					<span ng-if="berry.count != 1">berries</span>
					<span ng-if="berry.count == 1">berry</span>
					{{berry.perSec}}/s
				</td>
			</tr>
		</table>
	<br /><br /><br />
		<table>
			<!-- Sitrus Berry Pokemon -->
			<tr>
				<td ng-repeat="pokemonType in ['magikarp', 'charmander', 'bulbasaur', 'squirtle']" ng-include="'pokemonCell'"></td>
			</tr>
			 <!-- Leppa Berry Pokemon -->
			<tr>
				<td ng-repeat="pokemonType in ['pikachu', 'piplup', 'turtwig', 'weedle']" ng-include="'pokemonCell'"></td>
			</tr>
			<!-- Lum Berry Pokemon -->
			<tr>
				<td ng-repeat="pokemonType in ['pidgey', 'rattata', 'caterpie', 'ekans']" ng-include="'pokemonCell'"></td>
			</tr>
			<!-- Oran Berry Pokemon -->
			<tr>
				<td ng-repeat="pokemonType in ['vulpix', 'spearow', 'sandshrew', 'oddish']" ng-include="'pokemonCell'"></td>
			</tr>
			<!-- Enigma Berry Pokemon -->
			<tr>
				<td ng-repeat="pokemonType in ['diglett', 'poliwag', 'abra', 'machop']" ng-include="'pokemonCell'"></td>
			</tr>
			<!-- Pecha Berry Pokemon -->
			<tr>
				<td ng-repeat="pokemonType in ['bellsprout', 'tentacool', 'geodude', 'ponyta']" ng-include="'pokemonCell'"></td>
			</tr>
			<!-- Rawst Berry Pokemon -->
			<tr>
				<td ng-repeat="pokemonType in ['slowpoke', magnemite', 'doduo', 'seel']" ng-include="'pokemonCell'"></td>
			</tr>
            <!-- Coba Berry Pokemon -->
            <tr>
				<td ng-repeat="pokemonType in ['grimer', 'shellder', 'eevee', 'gastly']" ng-include="'pokemonCell'"></td>
			</tr>
            <!-- Custap Berry Pokemon -->
            <tr>
				<td ng-repeat="pokemonType in ['rhyhorn', 'horsea', 'dratini', 'snorlax']" ng-include="'pokemonCell'"></td>
			</tr>
		</table>

		<script type="text/ng-template" id="pokemonCell">
			<img ng-src="Images/{{pokemonType}}.png", ng-click="buyPokemon(pokemonType)">
			{{pokemonType | capitalize}}: {{gameData.pokemon[pokemonType].count}}<br />
			Cost: {{gameData.pokemon[pokemonType].nextCost}} {{gameData.pokemon[pokemonType].cost.berryType}} berries<br>
			<strong>Gives:</strong>
			<div ng-repeat="(berryType, berryQty) in gameData.pokemon[pokemonType].gives">
				{{berryQty}} {{berryType | capitalize}}
				<span ng-if="berryQty > 1">berries</span>
				<span ng-if="berryQty == 1">berry</span>
				per second.
			</div>
		</script>

		<br/><br/><br/>

		<img src="Images/reset.png" height='64' width='64' ng-click="resetGame()"/>
		Disclaimer: If there are new Pokemon that do not have any numbers or there is a type of berry that does not have any numbers, you will have to reset your game to get those working.

		<script src="bower_components/angular/angular.js"></script>
		<script type="text/javascript" src="main.js"></script>
        </div>
	</body>

</html>

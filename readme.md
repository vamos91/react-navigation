# ReactNative et navigation.
 
 React Native, tout comme React, est une librairie créée par Facebook. Il s’agit d’une déclinaison de React réservée aux mobiles.

## Une application en React Native utilisera :

**La librairie React** : on y retrouvera donc toute la gestion de React : la logique des composants, propriétés, états, inverse data flow, Redux, ..
La surcouche React Native qui adapte React aux fonctionnalités du smartphone
React Native va donc proposer un ensemble de composants clés en main pour pouvoir gérer les différents éléments graphiques du mobile ainsi qu’un ensemble de fonctionnalités liées aux devices (gestion de la vibration, récupération des informations de dimensions de l’écran, remontée si l’application est au premier plan ou non, etc)

### 1.1 Qu’est ce qui change avec React Native ?
Avec React, nous étions sur des applications web, il était donc possible d’utiliser les balises HTML (div, input, …). Avec React Native, nous nous affranchissons du navigateur : plus de balises HTML. Pour remplacer ces balises, React Native propose justement des composants et certaines propriétés pour remplacer le HTML :


```
<div> devient <View>
<p> devient <Text>
onClick devient onPress
```

### 1.2  Et Expo, c’est React Native ?
Expo est une suite d’outils open-source pour faciliter la création d’applications mobiles grâce à React Native. Expo propose tout un écosystème permettant de développer en React Native tout en ajoutant des briques clé en main pour simplifier le développement des applications mobiles.

Expo propose une librairie pour se brancher aux fonctionnalités natives du téléphone. Pour gérer l’appareil photo, afficher une map, utiliser le signin via Facebook par exemple, tout est directement proposé et géré par Expo que ce soit pour Android ou IOS.
Expo propose également d’émuler votre application directement sur votre mobile grâce à Expo Client, application installable sur votre smartphone.
Pas besoin de générer les applications via les environnements de développement. Xcode ou Android Studio pour les tester, nous pouvons les émuler directement sur le mobile.

Expo facilite également la publication de vos applications sur les différents stores et les mises à jour “à la volée” sans passer par une nouvelle validation de votre application.



## 2 - STEP BY STEP
On installe l’outil Expo en ligne de commande (ne pas oublier d’ajouter sudo devant la commande si vous êtes sous MacOS)
`npm install -g expo-cli`


On crée notre application (sélectionner “blank”)
`expo init monApplication --npm`


On rentre dans le répertoire généré
`cd monApplication`


On lance l’application
`expo start`

Un écran apparaît dans votre navigateur.

On installe Expo client sur son smartphone en se connectant sur le même réseau WiFi que son ordinateur
On scanne avec son smartphone le code barre affiché sur le navigateur
Avec l’appareil photo pour iOS ou directement avec l’application Expo sous Android. L’application va se builder et se lancer sur votre smartphone.

**Votre application est fonctionnelle !**

### 2.1  Un exemple de composant : App.js

```
import { StatusBar } from 'expo-status-bar';
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
return (
  <View style={styles.container}>
    <Text>Open up App.js to start working on your app!</Text>
    <StatusBar style="auto" />
  </View>
);
}

const styles = StyleSheet.create({
container: {
  flex: 1,
  backgroundColor: '#fff',
  alignItems: 'center',
  justifyContent: 'center',
},
});
```

### 2.1.1 On importe la status-bar proposée par expo

`import { StatusBar } from 'expo-status-bar';`

* Ce composant est proposé par expo pour configurer la barre de status de votre mobile.

Pour chaque fonctionnalité ou composant Expo, pensez à consulter la documentation fournie par Expo.

Elle nous donne des informations et des exemples d’utilisation  : https://docs.expo.io/versions/latest/sdk/status-bar/

### 2.1.2 On importe React

`import React from 'react';`

Avec React Native, nous utilisons les mécaniques de React. Nous avons besoin d’importer React.

### 2.1.3 On importe les composants de base proposés par React Native

`import { StyleSheet, Text, View } from 'react-native';`

Plus de HTML en React Native, nous importons les composants propres à React Native (<View> à la place de <div>, <Text> au lieu de <p> et StyleSheet pour le style).

On définit le style :

```
const styles = StyleSheet.create({
container: {
  flex: 1,
  backgroundColor: '#fff',
  alignItems: 'center',
  justifyContent: 'center',
},
});
```

On utilise StyleSheet pour créer un style “container” qui sera utilisé dans notre composant.

### 2.1.4 On crée notre composant App

```
export default function App() {
return (
  <View style={styles.container}>
    <Text>Open up App.js to start working on your app!</Text>
    <StatusBar style="auto" />
  </View>
);
}
```
On crée une View à laquelle  on applique le style “container”.

À l’intérieur de cette View, nous utilisons le composant <Text> ainsi que le composant <StatusBar>.



## 3 - CRASH SOUS MACOS
Dans certaines circonstances (version récente de l’OS, projet volumineux…), l’application peut subitement crasher sous MacOS avec le message suivant : “Error: EMFILE: too many open files, watch”

Voici les différentes étapes à suivre afin de régler définitivement ce problème en installant watchman, un utilitaire permettant de surveiller plus efficacement les modifications des fichiers au sein d’un projet React Native.

### 3.1  Installation du gestionnaire de package Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

### 3.2  Installation de l’utilitaire watchman
brew install watchman

**Attention : l’installation de ces deux programmes peut durer plusieurs minutes. Il vous suffira de relancer votre projet via la commande expo start 😉**




**CHALLENGE**

## 1 - NAVIGATION SIMPLE

👉Initialisez une nouvelle app appelée reactnaviation-stack-demo.

👉Créez 2 composants nommés "HomeScreen" et "PageAScreen".

👉Mettez la couleur de fond #e67e22 pour "HomeScreen" et #2ecc71 pour "PageAScreen".

👉Mettez en place les liens suivants :

- Un lien nommé "go to page A" sur "HomeScreen" permettant de rediriger l'utilisateur vers "PageAScreen"
- Un lien nommé "go to Home" sur "PageAScreen" permettant de rediriger l'utilisateur vers "HomeScreen"


## 2 - NAVIGATION AVEC MENU

👉 Initialisez une nouvelle app appelée reactnaviation-tabs-demo.

👉 Créez 2 composants nommés "HomeScreen" et "PageAScreen".

👉 Mettez la couleur de fond #9b59b6 pour "HomeScreen" et #3498db pour "PageAScreen".

👉 Liez les deux composants entre eux via un "Bottom Tab Navigator".

👉 Customisez le menu en y ajoutant deux icons. Utilisez le lien suivant pour avoir la liste complète des icons disponibles dans React Native : https://icons.expo.fyi/ 

- Sélectionnez l'icône "home" pour "HomeScreen".
- Sélectionnez l'icône "heart" pour "PageAScreen.



## 3 - MIXER LES DEUX TYPES DE NAVIGATION

Prenez bien le temps de comprendre cette mécanique afin de savoir comment créer et imbriquer les composants de navigation entre eux :

https://reactnavigation.org/docs/5.x/nesting-navigators 


👉 Initialisez une nouvelle app appelée reactnaviation-combo-demo.

👉 Créez 3 composants nommés "HomeScreen", "PageAScreen" et "PageBScreen".

👉 Mettez la couleur de fond #9b59b6 pour "HomeScreen", #3498db pour "PageAScreen" et #f1c40f pour "PageBScreen".

👉 Liez les composants "PageAScreen" et "PageBScreen" entre eux via un "Stack Navigator".

👉 Mettez en place les liens suivants :

* Un lien nommé "go to page B" sur "PageAScreen" permettant de rediriger l'utilisateur vers "PageBScreen".
* Un lien nommé "go to page A" sur "PageBScreen" permettant de rediriger l'utilisateur vers "PageAScreen".
* Sauvegardez la fonction stack navigator générée dans une variable nommée "StackNavigator".
* Créez un BottomTabNavigator qui sera retourné dans le composant App et qui inclura le StackNavigator précédemment créé (votre menu affichera 2 onglets : “Home” qui sera relié au composant HomeScreen et “PagesStacks” qui sera relié à votre variable StackNavigator)
👉 Customisez le menu en y ajoutant deux icons.

Sélectionnez l'icône "home" pour "HomeScreen".
Sélectionnez l'icône "heart" pour "PagesStack”.

👉 L'application permettra de récupérer le nom d'un user par le biais d'un formulaire dans HomeScreen. A l'aide du contexte de React, stockez le nom dans le store
Et afficher le nom dans "PageBScreen"



-----------------------------------------------------------------------------------------------------------------------------------------


# La géolocalisation.

**Expo propose un kit de développement pour accéder aux différentes fonctionnalités du device (Camera, Contacts, Géolocalisation, ...).**

**La documentation pour manipuler ces fonctionalités est disponible ici : https://docs.expo.io/versions/latest/**

L’avantage de ces fonctionnalités est qu’elles sont développées sous forme de module à installer dans son application. Chacun de ces modules va se plugger autant à IOS qu’Android pour nous permettre d’utiliser très simplement les fonctionnalités du mobile, peu importe l’OS.

__Pas besoin de développer pour iOS puis pour Android, l’API d’Expo s’occupe de tout !__




## 1.1 On peut intégrer les fonctionnalités de la map dans notre application ?
Expo offre effectivement la possibilité d’utiliser les fonctionnalités des Maps de chaque device.

La fonctionnalité à utiliser se nomme MapView : https://docs.expo.io/versions/latest/sdk/map-view/



MapView va utiliser les maps natives de chaque OS : pour iOS, nous allons pouvoir utiliser Plans alors que pour Android, ça sera Google Maps.

Si vous souhaitez utiliser Google Maps sur IOS, c’est également possible, tout est dans la documentation !

Autre avantage de MapView, la possibilité d’utiliser un ensemble de composants clés en main <MapView />, <Marker />, <Overlay />, …

Ces composants nous permettent de rajouter des fonctionnalités. Par exemple, placer des marqueurs sur la carte.

Tous ces composants sont personnalisables via leurs propriétés. Par exemple le composant MapView : https://github.com/react-native-maps/react-native-maps/blob/master/docs/mapview.md

## 1.2 Comment afficher la géolocalisation sur la carte ?
Là encore, Expo propose un module clé en main : Location

https://docs.expo.io/versions/latest/sdk/location/



Ce module va nous permettre de récupérer les informations de géolocalisation du téléphone.

Pour cela, il faudra que l’utilisateur nous donne l’autorisation de manipuler ces données de géolocalisation. Pas de problème, Expo vous offre des fonctions pour gérer cela simplement.

À partir du moment où notre application possède les droits, elle pourra récupérer la position de l’utilisateur une seule fois ou à intervalle régulier.

En utilisant les options de MapView et de Location, il nous sera possible d’afficher la position de l’utilisateur sur la carte par exemple.



# 2 - STEP BY STEP
## 2.1 Installer les modules pour MapView et la géolocalisation

expo install react-native-maps expo-location expo-permissions

Pour utiliser la map de chaque device, nous devons installer le module react-native-maps

```
Import du composant MapView
import MapView from 'react-native-maps';
```
Le composant MapView est proposé par react-native-maps pour afficher la map native de chaque device.

```
Initialisation de la map
<MapView style={{flex : 1}}
   initialRegion={{
     latitude: 37.78825,
     longitude: -122.4324,
     latitudeDelta: 0.0922,
     longitudeDelta: 0.0421,
   }}
 />
```

Nous pouvons personnaliser notre map en fournissant des informations sur sa région initiale :

Longitude et latitude qui correspondent aux informations pour centrer la carte.
latitudeDelta et longitudeDelta pour gérer le rayon à afficher à partir du centre.
Cela nous permet de gérer un niveau de zoom plus ou moins important. Plus ces informations sont grandes, plus le rayon sera important, plus on dézoomera.

## 2.2 Personnaliser la map
### 2.2.1 Modifier le type d’affichage
```
<MapView mapType ="satellite" />
```
Il existe plusieurs types de maps à afficher : satellite, standard, terrain, ...

### 2.2.2 Afficher les informations du trafic
```
<MapView showsTraffic ={true} />
```

### 2.2.3 Désactiver le zoom
```
<MapView zoomEnabled ={false} />
```

## 2.3 Afficher un marqueur
### 2.3.1 Import du composant Marker
```
import {Marker} from 'react-native-maps';
```

On importe le composant Marker de notre module.

Attention, ce composant n’est pas exporté par défaut, il faudra l’importer entre { }

### 2.3.2 Initialisation du composant
```
<MapView>
 <Marker
   coordinate={{latitude: 48.866667, longitude: 2.333333}}
 />
</MapView>
```

Le composant Marker va devoir être placé à l’intérieur du composant MapView.

Il faudra au minimum lui fournir un objet contenant la latitude et la longitude dans sa propriété coordinate.

## 2.4 Options du marqueur
### 2.4.1 Ajouter un titre et une description
```
<Marker
 coordinate={{latitude: 48.866667, longitude: 2.333333}}
 title="Hello"
 description="I am here"
/>
```
Le Marqueur sera personnalisable. On peut par exemple fournir d’autres propriétés comme title ou description.

### 2.4.2 Rendre le marqueur drag & dropable
```
<Marker
 coordinate={{latitude: 48.866667, longitude: 2.333333}}
 draggable
/>
```
La propriété draggable permet de rendre le marqueur drag&dropable, c’est-à-dire de donner la possibilité à l’utilisateur de le déplacer sur la map.

### 2.4.3 Modifier l’opacité

```
<Marker
 coordinate={{latitude: 48.866667, longitude: 2.333333}}
 opacity={0.5}
/>
```

## 2.5 Import des composants Location et Permissions
```
import * as Location from 'expo-location';
import * as Permissions from 'expo-permissions';
```

**Pour gérer la géolocalisation, nous devons importer les module expo-location et expo-permissions**

Pour utiliser la géolocalisation, il faut que l’utilisateur donne les droits à notre application. Nous devons donc créer une fonction qui demandera les droits et permettra ensuite dans ce cas à notre application de récupérer la position de l’utilisateur..
Permissions.askAsync(Permissions.LOCATION) demande l’autorisation et renvoie un objet contenant une propriété status. C’est cette information qui nous permet de savoir si nous avons les droits (granted). Attention, cette fonction est asynchrone. Nous allons donc temporiser la demande (await) et rendre notre fonction askPermissions asynchrone.
Si nous avons les droits, nous pouvons alors récupérer la position de l’utilisateur grâce à la fonction Location.getCurrentPositionAsync({}).
```
import React, {useEffect} from 'react';
import * as Location from 'expo-location';
import * as Permissions from 'expo-permissions';

export default function App() {
 useEffect(() => {
   async function askPermissions() {
     var { status } = await Permissions.askAsync(Permissions.LOCATION);
     if (status === 'granted') {
       var location = await Location.getCurrentPositionAsync({});
     }
   }
   askPermissions();
 }, []);

 return (
   <View>
     ...
   </View>
 );
}
```

### 2.5.1 On déclare une fonction pour demander l’autorisation

```
async function askPermissions() {
 var { status } = await Permissions.askAsync(Permissions.LOCATION);
 if (status === 'granted') {
   var location = await Location.getCurrentPositionAsync({});
 }
}
```

### 2.5.2 On exécute la fonction à l’initialisation de notre composant

```
useEffect(() => {
 async function askPermissions() {
   var { status } = await Permissions.askAsync(Permissions.LOCATION);
   if (status === 'granted') {
     var location = await Location.getCurrentPositionAsync({});
   }
 }
 askPermissions();
}, []);
```

La fonction askPermissions doit être exécutée à l’initialisation de notre composant. Nous l’appelons alors à l’intérieur d’un hook d’effet (useEffect) en précisant en deuxième argument que nous ne souhaitons l'exécuter qu’à l’initialisation [ ].

Dans cet exemple, nous récupérons les informations de géolocalisation qu’une seule fois, à l’initialisation de notre composant.

## 2.6 La géolocalisation en temps réel

```
import React, {useEffect} from 'react';
import * as Location from 'expo-location';
import * as Permissions from 'expo-permissions';

export default function App() {
 useEffect(() => {
   async function askPermissions() {
     let { status } = await Permissions.askAsync(Permissions.LOCATION);
     if (status === 'granted') {
       Location.watchPositionAsync({ distanceInterval: 10 },
         (location) => {
           console.log(location);
         }
       );
     }
   }
   askPermissions();
 }, []);

 return (
   <View>
     ...
   </View>
 );
}
```

### 2.6.1 On récupère la géolocalisation en temps réel

```
Location.watchPositionAsync({distanceInterval: 10},
 (location) => {
   console.log(location);
 }
);
```
Pour gérer la géolocalisation en temps réel, la mécanique est semblable à celle vue précédemment.

Un seul changement : nous allons mettre sur écoute la position de l’utilisateur pour que l’information nous soit remontée à chaque déplacement de l’utilisateur.

La mise sur écoute se fait avec la fonction Location.watchPositionAsync.

Nous pouvons paramétrer la distance à parcourir avant que notre téléphone nous remonte à nouveau la position de l'utilisateur. Ici une remontée sera faite tous les 10 mètres.

En deuxième argument, nous fournissons une fonction de callback. Celle-ci sera appelée tous les 10 mètres en fournissant en argument les informations de position de l’utilisateur (location).



# 3 - EN SAVOIR PLUS
## 3.1 Pour déployer son application ?
Expo vous propose une utilisation simplifiée de ses modules. Votre application va être facile à tester en l’émulant dans l’application Expo.

Attention, car l’application Expo possède déjà certains droits qu’il n’est pas nécessaire de configurer lorsqu’on émule notre application.

Par exemple, pour MapView, l’’application Expo a des droits pour utiliser Google Maps. Du coup, pas besoin de configurer votre application pour l’utiliser avec Expo.

Mais quand vous allez déployer votre application, vous ne passerez plus par Expo et votre application n’aura pas les droits d’exploiter Google Maps.

Pas d’inquiétude, Expo vous prévient et vous fournit la configuration à mettre en place pour que votre application fonctionne en standalone : https://docs.expo.io/distribution/building-standalone-apps/

Dans tous les cas, pensez à bien lire la documentation dans Expo !



# 1 - CHALLENGE

👉 Initialisez une nouvelle app appelée reactmap-findingnemo.

👉 Générez une map dans le composant App de l'app.

👉 Mettez en place un marqueur sur les coordonnées de la tour Eiffel (longitude:2.294481, latitude: 48.858370).

👉 Mettez en place une mécanique permettant de récupérer votre position (longitude, latitude) en temps réel.

👉 En utilisant un état nommé position, mettez à jour le composant grâce aux coordonnées reçues et matérialisez-les via un marqueur.



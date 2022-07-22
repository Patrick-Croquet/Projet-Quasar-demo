# Projet-Quasar-demo
 Projet Quasar demo

mkdir Projet-Quasar-demo
cd Projet-Quasar-demo
npm init -y

# Installons à présent la CLI du framework Quasar :
npm i @quasar/cli

# Créons le projet Quasar :
npx quasar create my-quasar-app

npm init quasar

√ What would you like to build? » App with Quasar CLI, let's go!        
App
√ Project description: ... A Quasar Framework app
√ Author: ... Patrick-Croquet <58164643+Patrick-Croquet@users.noreply.github.com>
√ Pick your CSS preprocessor: » Sass with SCSS syntax
√ Check the features needed for your project: » ESLint, State Management (Pinia), Axios
√ Pick an ESLint preset: » Prettier

cd my-quasar-app

Pour lancer votre application Quasar en mode développement, exécutez la commande :
npx quasar dev 

Pour créer l’application de production, il suffit d’exécuter la commande :
npx quasar build

# Lancer l’application mobile native iOS / Android
npx quasar mode add capacitor

*   Your Capacitor project is ready to go!  *
Add platforms using "npx cap add":

  npx cap add android
  npx cap add ios
  npx cap add electron

npx quasar dev -m capacitor -T [android|ios]

# Create Dekstop Application 
npx quasar dev -m electron

# Create Mobile Application
npm install -g cordova
npx quasar dev -m cordova -T android
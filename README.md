# ts-starter-kit

run following function in your shell:

```shell

function ts-starter-kit (){
  rm -rf ./*

  git clone https://github.com/Iicytower/ts-starter-kit.git

  mv -f ts-starter-kit/index.ts ./
  mv -f ts-starter-kit/tsconfig.json ./
  mv -f ts-starter-kit/.prettierrc ./
  mv -f ts-starter-kit/.prettierignore ./

  rm -rf ts-starter-kit

  npm init -y
  npm i -D typescript ts-node-dev prettier @types/node

  node -e "
  console.log('[LOG] Start modifying package.json... ');
  var fs = require('fs');
  var package = JSON.parse(fs.readFileSync('./package.json', 'utf8'));
  console.log('[LOG] Adding start script...');
  package.scripts.start='ts-node-dev --respawn index.ts'; 
  console.log('[LOG] Adding prettier script...');
  package.scripts.prettier='prettier -w ./**/*.ts'; 
  package.main='dist/index.js';
  fs.writeFileSync('./package.json', JSON.stringify(package, null, 2), 'utf8');
  console.log('[LOG] Work finished. :)');
  "
}

```
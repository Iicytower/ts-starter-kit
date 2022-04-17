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

  package=$(cat package.json);
  rm -rf ./package.json;

  echo $(echo $package | jq '.scripts |= {"prettier": "prettier -w ./**/*.ts", "start": "ts-node-dev --respawn index.ts"}') > indirectFile.json

  node -e "console.log(JSON.stringify(JSON.parse(require('fs').readFileSync(process.argv[1])), null, 2));" indirectFile.json > package.json

  rm -rf indirectFile.json
}

```
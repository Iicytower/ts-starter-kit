# ts-starter-kit

run following function in your shell:

```shell

function ts-starter-kit (){
  git clone https://github.com/Iicytower/ts-starter-kit.git

  mv -f ts-starter-kit/index.ts ./
  mv -f ts-starter-kit/tsconfig.json ./
  mv -f ts-starter-kit/.prettierrc ./
  mv -f ts-starter-kit/.prettierignore ./

  rm -rf ts-starter-kit

  npm init -y

  npm i -D typescript ts-node-dev prettier @types/node

  echo $(cat package.json | jq '.scripts |= {"prettier": "prettier -w ./**/*.ts", "start": "ts-node-dev --respawn index.ts"}') > package.json

}

```
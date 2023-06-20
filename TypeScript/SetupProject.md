# Setup project Typescrip with Nodejs

## Tài liệu tham khảo
[Setup](https://khalilstemmler.com/blogs/typescript/node-starter-project/)

1. `yarn init -y` or `npm init -y`
2. `yarn add typescript --dev` or `npm install typescirpt --save-dev`
3. `yarn add @types/node --dev` or `npm install @types/node --save-dev`
4. `yarn tsc --init --rootDir src --outDir build --esModuleInterop --resolveJsonModule --lib es6 --module commonjs --allowJs true --noImplicitAny true` or `npx tsc --init --rootDir src --outDir build --esModuleInterop --resolveJsonModule --lib es6 --module commonjs --allowJs true --noImplicitAny true`
5. Create `src`
6. Compiling with `yarn tsc` or `npx tsc`
7. `yarn add nodemon ts-node --dev` or `npm install nodemon ts-node --save-dev`
8. Add config in **nodemon.json**
    {
        "watch": ["src"],
        "ext": ".ts,.js",
        "ignore": [],
        "exec": "npx ts-node ./src/index.ts"
    }
9. Create production builds
    `yarn install --save-dev rimraf` or `npm install --save-dev rimraf`
    `"build": "rimraf ./build && tsc"` add in package.json

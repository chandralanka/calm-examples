## Install calm cli
npm install -g @finos/calm-cli

calm --version

## Install calm-server
npm install -g @finos/calm-server

npm install --save-dev @finos/calm-server

calm-server

## Install AI Agent
calm init-ai -p copilot -d .
calm init-ai -p claude

## Run Validations
calm validate -a architectures/ecommerce-platform.json

calm validate -p patterns/company-base-pattern.json -a architectures/ecommerce-platform.json -u url-mapping.json

## Docify
calm docify -a ./architectures/ecommerce-platform.json -o docs/generated

calm docify -a ./architectures/ecommerce-platform.json -o docs/output -u url-mapping.json

## Generate a custom Markdown report
calm docify -a ./architectures/ecommerce-platform.json -o reports/ -t my-report-template.hbs

calm docify -a ./architectures/ecommerce-platform.json -o reports/ -d my-templates/

## Run CALM Docs website
CD: docs\output
npm install
npm start

# calm-server
calm-server


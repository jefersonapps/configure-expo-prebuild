# Passo a Passo para Configurar o Ambiente e Rodar o Expo Prebuild no Android no Ubuntu 22.04.4 ou Pop!_OS 22.04 LTS

## Instalar o Android Studio e o SDK

- Baixe e instale o Android Studio pela loja do Sistema Operacional.
- Certifique-se de que o SDK foi instalado corretamente e localize o caminho do SDK (`/home/seu_usuario/Android/Sdk`).

## Configurar as variáveis de ambiente para o Android SDK:

- Edite o arquivo .bashrc para garantir que o caminho esteja correto:

```sh
nano ~/.bashrc
```

- Adicione (ou edite) as seguintes linhas, certificando-se de que o caminho está correto:

```sh
export ANDROID_HOME=/home/seu_usuario/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

- Salve e saia do editor (Ctrl+O para salvar e Ctrl+X para sair no nano).

## Aplicar as mudanças

Aplique as mudanças feitas no arquivo .bashrc:

```sh
source ~/.bashrc
```

## Instalar o JDK 17

- Adicione o repositório do JDK 17 e instale o JDK:

```sh
sudo add-apt-repository ppa:linuxuprising/java
sudo apt update
sudo apt install oracle-java17-installer oracle-java17-set-default
```

## Configurar a variável JAVA_HOME para o JDK 17

- Abra o arquivo .bashrc para edição novamente:

```sh
nano ~/.bashrc
```

- Adicione ou atualize a linha `export JAVA_HOME` para apontar para o JDK 17:

```sh
export JAVA_HOME=/usr/lib/jvm/java-17-oracle
export PATH=$PATH:$JAVA_HOME/bin
```

## Aplicar as mudanças novamente

Aplique as mudanças feitas no arquivo .bashrc:

```sh
source ~/.bashrc
```

## Verificar as configurações

- Verifique se as variáveis de ambiente estão configuradas corretamente:

```sh
echo $ANDROID_HOME
echo $JAVA_HOME
echo $PATH
```

- Certifique-se de que os caminhos estão corretos.
- Verificar a versão do Java:

```sh
java -version
```

A saída deve ser algo como:

```sh
java version "17.0.x" 2023-xx-xx LTS
Java(TM) SE Runtime Environment (build 17.0.x+xx)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.x+xx, mixed mode, sharing)
```

## Rodar o Expo Prebuild

1. Execute o comando no seu projeto Expo para criar as pastas `android` e `ios`:

```sh
npx expo prebuild
```

- Para compilar para Android, após a criação das pastas com o comando anterior, execute:

```sh
npx expo run:android
```

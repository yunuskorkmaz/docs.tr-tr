---
title: .NET uygulamalarını Raspberry PI 'ye dağıtma
description: .NET uygulamalarını Raspberry PI 'ye dağıtmayı öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96590049"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a>.NET uygulamalarını Raspberry PI 'ye dağıtma

.NET uygulamalarının Raspberry PI 'ye dağıtılması, diğer platformlardan de aynıdır. Uygulamanız, *kendi içinde* veya *çerçeveye bağımlı* Dağıtım modları olarak çalıştırılabilir. Her stratejinin avantajları vardır. Daha fazla bilgi için bkz. [.NET uygulama yayımlamaya genel bakış](../core/deploying/index.md).

## <a name="deploying-a-framework-dependent-app"></a>Çerçeveye bağımlı uygulama dağıtma

Uygulamanızı çerçeveye bağlı bir uygulama olarak dağıtmak için aşağıdaki adımları izleyin:

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. [DotNet-Install betiklerini](../core/tools/dotnet-install-script.md)kullanarak .net 'ı Raspberry PI 'ye yüklemeyin. Raspberry PI 'deki Bash isteminde aşağıdaki adımları uygulayın (yerel veya SSH):
    1. .NET yüklemek için aşağıdaki komutu çalıştırın:

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > Bu, en son sürümü yüklenir. Belirli bir sürüme ihtiyacınız varsa, sonuna ekleyin `--version <VERSION>` , burada `<VERSION>` belirli derleme sürümüdür.

    1. Yol çözünürlüğünü basitleştirmek için bir `DOTNET_ROOT` ortam değişkeni ekleyin ve *. DotNet* dizinini `$PATH` aşağıdaki komutlarla ekleyin:

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. Aşağıdaki komutla .NET yüklemesini doğrulayın:

        ```dotnetcli
        dotnet --version
        ```

        Görüntülenmiş sürümü yüklediğiniz sürümle eşleştirdiğini doğrulayın.

1. Geliştirme ortamına bağlı olarak uygulamayı geliştirme bilgisayarında aşağıdaki şekilde yayımlayın.
    - **Visual Studio** kullanıyorsanız, [uygulamayı yerel bir klasöre dağıtın](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019). Yayımlamadan önce, yayımlama profili özetindeki **Düzenle** ' yi seçin ve **Ayarlar** sekmesini seçin. **Dağıtım modunun** *çerçeveye bağımlı* olarak ayarlandığından ve **hedef çalışma zamanının** *Taşınabilir* olarak ayarlandığından emin olun.
    - **.Net CLI** kullanıyorsanız, [DotNet Publish](../core/tools/dotnet-publish.md) komutunu kullanın. Ek bağımsız değişken gerekmez.

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. Raspberry PI 'deki Bash isteminde (yerel veya SSH) uygulamayı çalıştırın. Bunu yapmak için, dağıtım klasörünü geçerli dizin olarak ayarlayın ve aşağıdaki komutu yürütün (burada *HelloWorld.dll* uygulamanın giriş noktasıdır):

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a>Kendi içinde uygulama dağıtma

Uygulamanızı kendi içinde bulunan bir uygulama olarak dağıtmak için aşağıdaki adımları izleyin:

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. Geliştirme ortamına bağlı olarak uygulamayı geliştirme bilgisayarında aşağıdaki şekilde yayımlayın.
    - **Visual Studio** kullanıyorsanız, [uygulamayı yerel bir klasöre dağıtın](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019). Yayımlamadan önce, yayımlama profili özetindeki **Düzenle** ' yi seçin ve **Ayarlar** sekmesini seçin. **Dağıtım modunun** *kendi içinde* ve **hedef çalışma zamanının** *Linux ARM* olarak ayarlandığından emin olun.
    - **.Net CLI** kullanıyorsanız, [DotNet Publish](../core/tools/dotnet-publish.md) komutunu `-r linux-arm` bağımsız değişkenle kullanın:

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. Raspberry PI 'deki Bash isteminde (yerel veya SSH) uygulamayı çalıştırın. Bunu yapmak için, geçerli dizini dağıtım konumuna ayarlayın ve aşağıdaki adımları uygulayın:
    1. Yürütülebilir *yürütme* iznini (burada `HelloWorld` yürütülebilir dosya adıdır) verir.

        ```bash
        chmod +x HelloWorld
        ```

    1. Yürütülebilir dosyayı çalıştırın.

        ```bash
        ./HelloWorld
        ```

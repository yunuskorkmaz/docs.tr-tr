---
title: Visual Studio Code kullanarak bir .NET Core konsol uygulaması yayımlama
description: Yayımlama, .NET Core uygulamasını çalıştırmak için gereken dosya kümesini oluşturur.
ms.date: 07/04/2020
ms.openlocfilehash: a84e66126806e2ab45c14527df1b931fa9980468
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867652"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a>Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması yayımlama

Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir. Yayımlama, bir uygulamayı çalıştırmak için gereken dosyalar kümesini oluşturur. Dosyaları dağıtmak için, onları hedef makineye kopyalayın.

.NET Core CLI, uygulamayı yayımlamak için kullanılır, bu nedenle bu öğreticiyi Visual Studio Code dışında bir kod düzenleyicisiyle takip edebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- Bu öğretici, [Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.

## <a name="publish-the-app"></a>Uygulamayı yayımlama

1. Visual Studio Code’u başlatma.

1. [Visual Studio Code kullanarak .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz *HelloWorld* proje klasörünü açın.

1. Ana menüden **Görünüm**  >  **terminali** ' ni seçin.

   Terminal *HelloWorld* klasöründe açılır.

1. Aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   Varsayılan derleme yapılandırması *hata ayıklayın*, bu nedenle bu komut *yayın* derleme yapılandırmasını belirtir. Yayın derleme yapılandırmasından alınan çıktıda minimum sembolik hata ayıklama bilgileri bulunur ve tamamen iyileştirilmiştir.

   Komut çıktısı aşağıdaki örneğe benzer:

   ```output
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a>Dosyaları inceleyin

Varsayılan olarak, yayımlama işlemi, yayımlanan uygulamanın .NET Core çalışma zamanı yüklü bir makinede çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur. Yayımlanan uygulamayı çalıştırmak için yürütülebilir dosyayı kullanabilir veya komutu `dotnet HelloWorld.dll` komut isteminden çalıştırabilirsiniz.

Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.

1. Sol gezinti çubuğunda **Gezgin** ' i seçin.

1. *Bin/Release/netcoreapp 3.1/Yayımla*' yı genişletin.

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Yayımlanan dosyaları gösteren gezgin":::

   Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:

   * * ÜzerindeHelloWorld.deps.js*

      Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır. Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar. Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

   * *HelloWorld.dll*

      Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür. Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin. Uygulamayı çalıştırma yöntemi, .NET Core çalışma zamanının yüklü olduğu tüm platformlarda çalışır.

   * *HelloWorld.exe* (Linux üzerinde*HelloWorld* , MacOS 'ta oluşturulmaz.)

      Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür. Dosya işletim sistemine özgüdür.

   * *HelloWorld. pdb* (dağıtım için isteğe bağlı)

      Bu, hata ayıklama sembolleri dosyasıdır. Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.

   * * ÜzerindeHelloWorld.runtimeconfig.js*

      Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır. Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar. Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz. Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Yayımlanan uygulamayı çalıştırma

1. **Gezgin**'de *Yayımla* klasörüne sağ tıklayın (MacOS ' a<kbd>CTRL tuşunu basılı</kbd>olarak) ve **terminalde aç**' ı seçin.

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Terminalde aç 'ı gösteren bağlam menüsü":::

1. Windows veya Linux 'ta, yürütülebilir dosyayı kullanarak uygulamayı çalıştırın.

   1. Windows 'ta yazın `.\HelloWorld.exe` ve ENTER tuşuna <kbd>Enter</kbd>basın.

   1. Linux 'ta yazın `./HelloWorld` ve ENTER tuşuna <kbd>Enter</kbd>basın.

   1. İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.

1. Herhangi bir platformda, komutunu kullanarak uygulamayı çalıştırın  [`dotnet`](../tools/dotnet.md) :

   1. Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>Enter</kbd>tuşuna basın.

   1. İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.

## <a name="additional-resources"></a>Ek kaynaklar

- [.NET Core uygulama dağıtımı](../deploying/index.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir konsol uygulaması yayımladınız. Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.

> [!div class="nextstepaction"]
> [Visual Studio Code kullanarak .NET Standard kitaplığı oluşturma](library-with-visual-studio-code.md)

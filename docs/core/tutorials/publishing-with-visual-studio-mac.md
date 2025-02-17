---
title: Mac için Visual Studio kullanarak bir .NET konsol uygulaması yayımlama
description: .NET uygulamasını çalıştırmak için gereken dosya kümesini oluşturmak için Mac için Visual Studio nasıl kullanacağınızı öğrenin.
ms.date: 11/30/2020
ms.openlocfilehash: 88f143011b19ca8eda6610803c894e619d06a635
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599198"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio-for-mac"></a>Öğretici: Mac için Visual Studio kullanarak bir .NET konsol uygulaması yayımlama

Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir. Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur. Dosyaları dağıtmak için, onları hedef makineye kopyalayın.

## <a name="prerequisites"></a>Önkoşullar

- Bu öğretici, [Mac için Visual Studio kullanarak bir .NET konsol uygulaması oluşturma](with-visual-studio-mac.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.

## <a name="publish-the-app"></a>Uygulamayı yayımlama

1. Mac için Visual Studio başlatın.

1. [Mac için Visual Studio kullanarak .NET konsol uygulaması oluşturma](with-visual-studio-mac.md)bölümünde oluşturduğunuz HelloWorld projesini açın.

1. Visual Studio 'nun uygulamanızın yayın sürümünü oluşturmakta olduğundan emin olun. Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release** olarak değiştirin.

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Yayın derlemesi seçiliyken Visual Studio araç çubuğu":::

1. Ana menüden **derleme** Yayımla klasörü ' ne tıklayın.  >  **..**

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Visual Studio Yayımla bağlam menüsü":::

1. **Klasöre Yayımla** Iletişim kutusunda **Yayımla**' yı seçin.

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Visual Studio klasöre Yayımla iletişim kutusu":::

   Oluşturulan dosyaları gösteren Yayımla klasörü açılır.

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="klasörü Yayımla":::

1. Dişli simgesini seçin ve bağlam menüsünden **"Yayımla" adını yol adı olarak Kopyala** ' yı seçin.

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Yayımlama klasörünün yolunu Kopyala":::

## <a name="inspect-the-files"></a>Dosyaları inceleyin

Yayımlama işlemi, yayımlanan uygulamanın .NET çalışma zamanının yüklü olduğu bir makinede çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur. Kullanıcılar, komut isteminden komutunu çalıştırarak yayımlanmış uygulamayı çalıştırabilir `dotnet HelloWorld.dll` .

Önceki görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:

* *ÜzerindeHelloWorld.deps.js*

  Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır. Uygulamayı çalıştırmak için gereken .NET bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar. Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

* *HelloWorld.dll*

   Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür. Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin. Uygulamayı çalıştırma yöntemi, .NET çalışma zamanının yüklü olduğu tüm platformlarda çalışır.

* *HelloWorld. pdb* (dağıtım için isteğe bağlı)

   Bu, hata ayıklama sembolleri dosyasıdır. Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.

* *ÜzerindeHelloWorld.runtimeconfig.js*

   Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır. Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET sürümünü tanımlar. Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz. Daha fazla bilgi için bkz. [.NET çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Yayımlanan uygulamayı çalıştırma

1. Bir Terminal açın ve *Yayımla* klasörüne gidin. Bunu yapmak için, `cd` daha önce kopyaladığınız yolu girin ve yapıştırın. Örnek:

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/net5.0/publish/
   ```

1. Şu komutu kullanarak uygulamayı çalıştırın `dotnet` :

   1. Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>enter</kbd>tuşuna basın.

   1. İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.

## <a name="additional-resources"></a>Ek kaynaklar

- [.NET uygulama dağıtımı](../deploying/index.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir konsol uygulaması yayımladınız. Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.

> [!div class="nextstepaction"]
> [Mac için Visual Studio kullanarak bir .NET kitaplığı oluşturma](library-with-visual-studio-mac.md)

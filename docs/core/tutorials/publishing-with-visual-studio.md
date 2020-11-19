---
title: Visual Studio kullanarak bir .NET konsol uygulaması yayımlama
description: .NET uygulamasını çalıştırmak için gereken dosya kümesini oluşturmak için Visual Studio 'Yu nasıl kullanacağınızı öğrenin.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: b0c6bd85ddf86f0eb11c56f01abb74a7e9786363
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916035"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio"></a>Öğretici: Visual Studio kullanarak bir .NET konsol uygulaması yayımlama

Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir. Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur. Dosyaları dağıtmak için, onları hedef makineye kopyalayın.

## <a name="prerequisites"></a>Önkoşullar

- Bu öğretici, [Visual Studio kullanarak bir .NET konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.

## <a name="publish-the-app"></a>Uygulamayı yayımlama

1. Visual Studio’yu çalıştırın.

1. [Visual Studio kullanarak .NET konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz *HelloWorld* projesini açın.

1. Visual Studio 'Nun yayın derleme yapılandırması ' nı kullandığınızdan emin olun. Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release** olarak değiştirin.

   :::image type="content" source="media/publishing-with-visual-studio/visual-studio-toolbar-release.png" alt-text="Yayın derlemesi seçiliyken Visual Studio araç çubuğu":::

1. **HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin.

   :::image type="content" source="media/publishing-with-visual-studio/publish-context-menu.png" alt-text="Visual Studio Yayımla bağlam menüsü":::

1. **Yayımla** sayfasının **hedef** sekmesinde **klasör**' i seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/publishing-with-visual-studio/pick-publish-target.png" alt-text="Visual Studio 'da bir yayımlama hedefi seçin":::

1. **Yayımla** sayfasının **belirli hedef** sekmesinde **klasör**' i seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/publishing-with-visual-studio/pick-specific-publish-target.png" alt-text="Visual Studio 'da belirli yayımlama hedefini seçme":::

1. **Yayımla** sayfasının **konum** sekmesinde **son**' u seçin.

   :::image type="content" source="media/publishing-with-visual-studio/publish-page-loc-tab.png" alt-text="Visual Studio yayımlama sayfası konum sekmesi":::

1. **Yayımla** penceresinin **Yayımla** sekmesinde **Yayımla**' yı seçin.

   :::image type="content" source="media/publishing-with-visual-studio/publish-page.png" alt-text="Visual Studio Yayımla penceresi":::

## <a name="inspect-the-files"></a>Dosyaları inceleyin

Varsayılan olarak, yayımlama işlemi, yayımlanan uygulamanın .NET çalışma zamanının yüklü olduğu makinede çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur. Kullanıcılar, çalıştırılabilir dosyayı çift tıklayarak veya komut isteminden komutu vererek, yayımlanan uygulamayı çalıştırabilir `dotnet HelloWorld.dll` .

Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.

1. **Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.

1. Proje klasöründe, *bin/Release/net 5.0/Publish*' ı genişletin.

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Yayımlanan dosyaları gösterme Çözüm Gezgini":::

   Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:

   * *ÜzerindeHelloWorld.deps.js*

      Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır. Uygulamayı çalıştırmak için gereken .NET bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar. Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

   * *HelloWorld.dll*

      Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür. Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin. Uygulamayı çalıştırma yöntemi, .NET çalışma zamanının yüklü olduğu tüm platformlarda çalışır.

   * *HelloWorld.exe*

      Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür. Çalıştırmak için `HelloWorld.exe` bir komut istemine girin. Dosya işletim sistemine özgüdür.

   * *HelloWorld. pdb* (dağıtım için isteğe bağlı)

      Bu, hata ayıklama sembolleri dosyasıdır. Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.

   * *ÜzerindeHelloWorld.runtimeconfig.js*

      Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır. Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET sürümünü tanımlar. Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz. Daha fazla bilgi için bkz. [.NET çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Yayımlanan uygulamayı çalıştırma

1. **Çözüm Gezgini**, *Yayımla* klasörüne sağ tıklayın ve **tam yolu Kopyala**' yı seçin.

1. Bir komut istemi açın ve *Yayımla* klasörüne gidin. Bunu yapmak için `cd` tam yolu girin ve ardından yapıştırın. Örnek:

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. Yürütülebilir dosyayı kullanarak uygulamayı çalıştırın:

   1. Yazın `HelloWorld.exe` ve ENTER <kbd>Enter</kbd>tuşuna basın.

   1. İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.

1. Şu komutu kullanarak uygulamayı çalıştırın `dotnet` :

   1. Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>Enter</kbd>tuşuna basın.

   1. İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.

## <a name="additional-resources"></a>Ek kaynaklar

- [.NET uygulama dağıtımı](../deploying/index.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir konsol uygulaması yayımladınız. Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.

> [!div class="nextstepaction"]
> [Visual Studio kullanarak .NET sınıf kitaplığı oluşturma](library-with-visual-studio.md)

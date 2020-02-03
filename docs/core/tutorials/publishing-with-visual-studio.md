---
title: .NET Core Merhaba Dünya uygulamanızı Visual Studio ile yayımlama
description: Yayımlama, .NET Core uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: a82934fd2ea9568681a3bec82c3b15513decc926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741570"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>.NET Core Merhaba Dünya uygulamanızı Visual Studio ile yayımlama

[Visual Studio 'da .NET Core ile Merhaba Dünya uygulaması oluşturma](with-visual-studio.md)bölümünde, bir Merhaba Dünya konsol uygulaması oluşturacaksınız. [Visual Studio ile Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md)yaparken, Visual Studio hata ayıklayıcısını kullanarak test edersiniz. Artık beklendiği gibi çalıştığından emin olduğunuza göre, diğer kullanıcıların çalıştırabilmesi için onu yayımlayabilirsiniz. Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur. Dosyaları dağıtmak için, onları hedef makineye kopyalayın.

## <a name="publish-the-app"></a>Uygulamayı yayımlama

1. Visual Studio 'nun uygulamanızın yayın sürümünü oluşturmakta olduğundan emin olun. Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release**olarak değiştirin.

   ![Yayın derlemesi seçiliyken Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. **HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin. (Ana **Yapı** menüsünden **HelloWorld Yayımla** ' yı da seçebilirsiniz.)

   ![Visual Studio Yayımla bağlam menüsü](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. **Bir yayımlama hedefi** seçin sayfasında **klasör**' i seçin ve ardından **Profil oluştur**' u seçin.

   ![Visual Studio 'da bir yayımlama hedefi seçin](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. **Yayımla** sayfasında **Yayımla**' yı seçin.

   ![Visual Studio Yayımla penceresi](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a>Dosyaları inceleyin

Yayımlama işlemi, yayımlanmış uygulamanın sistemde .NET Core tarafından desteklenen herhangi bir platformda çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur. Kullanıcılar çalıştırılabilir dosyayı çift tıklayarak veya bir komut isteminden `dotnet HelloWorld.dll` komutunu yayımlayarak, yayımlanan uygulamayı çalıştırabilir.

Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.

1. Bir komut istemi açın.

   Komut istemi açmak için bir yol, Windows görev çubuğundaki arama kutusuna **komut istemi** (veya Short için **cmd** ) girmenin bir yoludur. Masaüstü uygulamasını **komut istemi** ' ni seçin veya arama sonuçlarında zaten seçiliyse **ENTER** tuşuna basın.

1. Uygulamanın proje dizininin *Bin\release\netcoreapp3.1\publish* alt dizininde yayınlanan uygulamaya gidin.

   ![Yayımlanan dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/published-files-output.png)

   Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:

      * *HelloWorld. Deps. JSON*

         Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır. Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar. Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld. dll*

         Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür. Bu dinamik bağlantı kitaplığını yürütmek için, komut istemine `dotnet HelloWorld.dll` girin.

      * *HelloWorld. exe*
      
         Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür. Çalıştırmak için, komut istemine `HelloWorld.exe` girin.

      * *HelloWorld. pdb* (dağıtım için isteğe bağlı)

         Bu, hata ayıklama sembolleri dosyasıdır. Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.

      * *HelloWorld. runtimeconfig. JSON*

         Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır. Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar. Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz. Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

## <a name="additional-resources"></a>Ek kaynaklar

- [.NET Core uygulama dağıtımı](../deploying/index.md)

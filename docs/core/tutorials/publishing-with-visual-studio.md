---
title: .NET Core Hello World uygulamanızı Visual Studio ile yayınlayın
description: Yayımlama, .NET Core uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156640"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>.NET Core Hello World uygulamanızı Visual Studio ile yayınlayın

[Visual Studio'da .NET Core ile Hello World uygulaması oluşturun,](with-visual-studio.md)Hello World konsol uytun. [Visual Studio ile Hello World uygulama hata ayıklama](debugging-with-visual-studio.md)olarak, Visual Studio hata ayıklama kullanarak test etti. Beklendiği gibi çalıştığından emin olduğunuza göre, diğer kullanıcıların çalıştırabilmesi için yayımlayabilirsiniz. Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur. Dosyaları dağıtmak için, bunları hedef makineye kopyalayın.

## <a name="publish-the-app"></a>Uygulamayı yayımlama

1. Visual Studio'nun uygulamanızın Sürüm sürümünü oluşturmadığından emin olun. Gerekirse, araç çubuğundaki yapı yapılandırma ayarını **Hata Ayıklama'dan** **Release'e**değiştirin.

   ![Sürüm yapısı seçili Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. **HelloWorld** projesine (HelloWorld çözümü değil) sağ tıklayın ve menüden **Yayınla'yı** seçin. (Ana **Yapı** menüsünden **HelloWorld'ü** Yayımla'yı da seçebilirsiniz.)

   ![Visual Studio Bağlam menüsünü yayımla](media/publishing-with-visual-studio/publish-context-menu.png)

1. **Yayımlama hedef** sayfasını seç'te **Klasör'ü**seçin ve ardından **Profil Oluştur'u**seçin.

   ![Visual Studio'da bir yayımlama hedefi seçin](media/publishing-with-visual-studio/pick-publish-target.png)

1. **Yayımla** sayfasında **Yayımla'yı**seçin.

   ![Visual Studio Yayımlama penceresi](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Dosyaları inceleyin

Yayımlama işlemi, yayımlanan uygulamanın .NET Core tarafından desteklenen ve .NET Core tarafından desteklenen ve sistemde yüklü olan herhangi bir platformda çalıştığı bir dağıtım türü olan çerçeveye bağımlı bir dağıtım oluşturur. Kullanıcılar, çalıştırılabilir uygulamayı çift tıklatarak veya `dotnet HelloWorld.dll` komut isteminden komut vererek yayınlanan uygulamayı çalıştırabilir.

Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.

1. Bir komut istemi açın.

   Komut istemini açmanın bir yolu, Windows görev çubuğundaki arama kutusuna **Komut İstemi** (veya kısaca **cmd)** girmektir. Komut **İstem** masaüstü uygulamasını seçin veya arama sonuçlarında zaten seçiliyse **Enter** tuşuna basın.

1. *Bin\Release\netcoreapp3.1\publish* alt dizininde yayınlanan uygulamaya gidin.

   ![Yayımlanmış dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/published-files-output.png)

   Resimde görüldüğü gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:

      * *HelloWorld.deps.json*

         Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır. Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar. Daha fazla bilgi için [Runtime yapılandırma dosyalarına](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)bakın.

      * *HelloWorld.dll*

         Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür. Bu dinamik bağlantı kitaplığını `dotnet HelloWorld.dll` yürütmek için komut istemiyle girin.

      * *MerhabaWorld.exe*

         Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür. Çalıştırmak için komut `HelloWorld.exe` istemiyle girin.

      * *HelloWorld.pdb* (dağıtım için isteğe bağlı)

         Bu hata ayıklama sembolleri dosyasıdır. Uygulamanızın yayımlanmış sürümünü hata ayıklamanız gerektiğinde bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez.

      * *HelloWorld.runtimeconfig.json*

         Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır. Uygulamanızın üzerinde çalışmak üzere oluşturulmuş olduğu .NET Core sürümünü tanımlar. Yapılandırma seçenekleri de ekleyebilirsiniz. Daha fazla bilgi için [.NET Core çalışma zamanı yapılandırma ayarlarına](../run-time-config/index.md#runtimeconfigjson)bakın.

## <a name="additional-resources"></a>Ek kaynaklar

- [.NET Core uygulama dağıtımı](../deploying/index.md)

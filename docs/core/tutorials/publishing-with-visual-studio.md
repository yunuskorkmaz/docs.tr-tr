---
title: .NET Core Merhaba Dünya uygulamanızı Visual Studio 2017 ile yayımlama
description: Yayımlama, .NET Core uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f8c37f47cc8dfb999f2371773a50c2dd91e074a5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660482"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>.NET Core Merhaba Dünya uygulamanızı Visual Studio 2017 ile yayımlama

Visual [studio 2017 C# ' de .net Core ile Merhaba Dünya bir uygulama oluşturun](with-visual-studio.md) veya [Visual Studio 2017 ' de .NET Core ile Visual Basic Merhaba Dünya uygulaması oluşturun](vb-with-visual-studio.md)Merhaba Dünya konsol uygulaması oluşturacaksınız. [Visual studio 2017 C# Ile Merhaba Dünya uygulamanızda hata ayıklayın](debugging-with-visual-studio.md), Visual Studio hata ayıklayıcısını kullanarak test edersiniz. Artık beklendiği gibi çalıştığından emin olduğunuza göre, diğer kullanıcıların çalıştırabilmesi için onu yayımlayabilirsiniz. Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur ve dosyaları bir hedef makineye kopyalayarak dağıtabilirsiniz.

Uygulamanızı yayımlamak ve çalıştırmak için: 

1. Visual Studio 'nun uygulamanızın yayın sürümünü oluşturmakta olduğundan emin olun. Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release**olarak değiştirin.

   ![Yayın derlemesi seçiliyken Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. **HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin. Ana Visual Studio **Build** menüsünden **HelloWorld Yayımla** ' yı da seçebilirsiniz.

   ![Visual Studio Yayımla bağlam menüsü](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Visual Studio Yayımla penceresi](media/publishing-with-visual-studio/publish-settings-window.png)

1. Bir konsol penceresi açın. Örneğin, burada, Windows görev çubuğundaki metin kutusuna **aramak için yazın** , (veya `cmd` kısaca `Command Prompt` ) girin ve **komut istemi** masaüstü uygulamasını seçerek veya ' de seçili ise ENTER tuşuna basarak bir konsol penceresi açın. Arama sonuçları.

1. Uygulamanızın proje dizininin `bin\release\PublishOutput` alt dizininde yayınlanan uygulamaya gidin. Aşağıdaki şekilde gösterildiği gibi, yayımlanan çıktı aşağıdaki dört dosyayı içerir:

      * *HelloWorld. Deps. JSON*

         Uygulamanın çalışma zamanı bağımlılıkları dosyası. Uygulamanızı çalıştırmak için gerekli olan .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar. Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld. dll*

         Uygulamanızı içeren dosya. Bir konsol penceresinde `dotnet HelloWorld.dll` komut girilerek yürütülebilecek bir dinamik bağlantı kitaplığıdır. 

      * *HelloWorld. pdb* (dağıtım için isteğe bağlı)

         Hata ayıklama sembolleri içeren bir dosya. Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.

      * *HelloWorld. runtimeconfig. JSON*

         Uygulamanın çalışma zamanı yapılandırma dosyası. Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar. Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Yayımlanan dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/published-files-output.png)

Yayımlama işlemi, yayımlanan uygulamanın .NET Core tarafından sistemde yüklü olan herhangi bir platformda çalışacağı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur. Kullanıcılar, `dotnet HelloWorld.dll` bir konsol penceresinden komutu yayımlayarak uygulamanızı çalıştırabilir.

.NET Core uygulamalarını yayımlama ve dağıtma hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

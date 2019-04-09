---
title: Visual Studio 2017 ile .NET Core Merhaba Dünya uygulamanızı yayımlama
description: Yayımlama, .NET Core uygulamanızı çalıştırmak için gereken dosyaları kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0322d44ca37ab8e7faa3188887069c2e04ec755b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110272"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>Visual Studio 2017 ile .NET Core Merhaba Dünya uygulamanızı yayımlama

İçinde [Visual Studio 2017'de .NET Core ile bir C# Merhaba Dünya uygulaması derleme](with-visual-studio.md) veya [Visual Studio 2017'de .NET Core ile bir Visual Basic Merhaba Dünya uygulaması derleme](vb-with-visual-studio.md), bir Hello World konsol uygulamanızı oluşturdunuz . İçinde [Visual Studio 2017 ile C# Merhaba Dünya uygulamanızın hatalarını](debugging-with-visual-studio.md), Visual Studio hata ayıklayıcısını kullanarak test. Artık beklendiği gibi çalıştığından emin olduğunuza göre diğer kullanıcıların çalıştırabilmek yayımlayabilirsiniz. Uygulamanızı çalıştırmak için gereken dosyaları kümesini yayımlama oluşturur ve bir hedef makineye kopyalayarak dosyaları dağıtabilirsiniz.

Yayımlama ve uygulamanızı çalıştırmak için: 

1. Visual Studio, uygulamanızın sürümünü oluşturuyor emin olun. Gerekirse araç çubuğundaki derleme yapılandırma ayarını değiştirme **hata ayıklama** için **yayın**.

   ![Visual Studio araç çubuğunda seçilen yayın derlemesi](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Sağ **HelloWorld** seçin ve proje (HelloWorld çözümü değil) **Yayımla** menüsünde. Belirleyebilirsiniz **yayımlama HelloWorld** ana Visual Studio'dan **derleme** menüsü.

   ![Visual Studio Yayımla bağlam menüsü](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Visual Studio yayımlama penceresi](media/publishing-with-visual-studio/publish-settings-window.png)

1. Bir konsol penceresi açın. Örneğin **aramak için buraya yazın** metin kutusunda Windows görev çubuğunda, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açıyor **komut istemi** Masaüstü uygulama veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.

1. Yayımlanan uygulamayı gidin `bin\release\PublishOutput` uygulamanızın proje dizininin alt. Aşağıdaki şekilde gösterildiği gibi yayımlanmış çıktısı aşağıdaki dört dosyaları içerir:

      * *HelloWorld.deps.json*

         Uygulamanın çalışma zamanı bağımlılıkları dosyası. .NET Core bileşenlerinin tanımlar ve kitaplıkları (uygulamanızı içeren bir dinamik bağlantı kitaplığı dahil), uygulamanızı çalıştırmak gerekli. Daha fazla bilgi için [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Uygulamanızı içeren dosya. Girerek yürütülebilecek bir dinamik bağlantı kitaplığı, `dotnet HelloWorld.dll` konsol penceresinde komutu. 

      * *HelloWorld.pdb* (dağıtım için isteğe bağlı)

         Hata ayıklama sembollerini içeren dosya. Uygulamanızın yayımlanmış sürümünün hata ayıklama yapmanız durumunda, kaydetmeniz gerekir ancak bu dosya, uygulamanızın yanı sıra dağıtmak için gerekli değildir.

      * *HelloWorld.runtimeconfig.json*

         Uygulamanın çalışma zamanı yapılandırma dosyası. Bu, uygulamanızı çalıştırmak için oluşturulmuş bir .NET Core sürümünü tanımlar. Daha fazla bilgi için [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Yayımlanan dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/published-files-output.png)

Yayımlama işlemi dağıtım türünde yayımlanan uygulama için sistemde yüklü .NET Core ile .NET Core tarafından desteklenen herhangi bir platformda çalıştıracağınız bir framework bağımlı dağıtımı oluşturur. Kullanıcılar, uygulamanızı yayımlayarak çalıştırabilirsiniz `dotnet HelloWorld.dll` bir konsol penceresi komutu.

.NET Core uygulamaları dağıtma ve yayımlama hakkında daha fazla bilgi için bkz. [.NET Core uygulaması dağıtımını](../../core/deploying/index.md).

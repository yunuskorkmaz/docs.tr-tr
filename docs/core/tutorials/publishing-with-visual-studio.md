---
title: Visual Studio 2017 Hello World uygulamanızla yayımlama
description: Yayımlama uygulamanızı çalıştırmak için gerekli dosyaları kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.openlocfilehash: 11421c8820dd562ba1dbb5900ba1e9bf944b45d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212137"
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a>Visual Studio 2017 Hello World uygulamanızla yayımlama

İçinde [bir C# Hello World uygulamasının Visual Studio 2017 .NET çekirdek ile yapı](with-visual-studio.md) veya [.NET Core Visual Studio 2017'de Visual Basic Hello World uygulamayla yapı](vb-with-visual-studio.md), Hello World konsol uygulaması yerleşik . İçinde [Visual Studio 2017 ile C# Hello World uygulamanızda hata ayıklama](debugging-with-visual-studio.md), Visual Studio hata ayıklayıcısı kullanarak test. Beklendiği gibi çalıştığını emin, diğer kullanıcılar bunu çalıştırabilmeniz için yayımlayabilirsiniz. Uygulamanızı çalıştırmak için gerekli dosyaları kümesini yayımlama oluşturur ve bir hedef makine kopyalayarak dosyaları dağıtabilirsiniz.

Yayımlama ve uygulamanızı çalıştırmak için: 

1. Visual Studio sürümü, uygulamanızın oluşturuyor emin olun. Gerekirse, araç çubuğundaki derleme yapılandırma ayarını değiştirme **hata ayıklama** için **sürüm**.

   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/toolbar.png)

1. Sağ **HelloWorld** proje (HelloWorld çözümü değil) ve seçin **Yayımla** menüsünde. Öğesini de seçebilirsiniz **yayımlama HelloWorld** ana Visual Studio'dan **yapı** menüsü.

   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/publishwindow.png)

1. Bir konsol penceresi açın. Örneğin **aramak için buraya yazın** metin kutusunda Windows görev çubuğundaki, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açın **komut istemi** Masaüstü uygulama veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.

1. Yayımlanan uygulamayı gidin `bin\release\PublishOutput` uygulamanızın proje dizininin alt. Aşağıdaki şekilde gösterildiği gibi yayımlanmış çıktı aşağıdaki dört dosya içerir:

      * *HelloWorld.deps.json*

         Uygulamanın çalışma zamanı bağımlılıkları dosyası. .NET Core bileşenleri tanımlar ve (uygulamanızın içeren dinamik bağlantı kitaplığı dahil) kitaplıkları uygulamanızı çalıştırmak için gerekli. Daha fazla bilgi için bkz: [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Uygulamanızı içeren dosya. Girerek yürütülebilir bir dinamik bağlantı kitaplığı olan `dotnet HelloWorld.dll` bir konsol penceresinde komutu. 

      * *HelloWorld.pdb* (dağıtım için isteğe bağlı)

         Hata ayıklama simgeleri içeren dosya. Yayımlanmış bir sürüm, uygulamanızın hatalarını ayıklama gerek gerektiğinde, kaydetmelisiniz rağmen bu dosya, uygulamanızın birlikte dağıtmak için gerekli değil.

      * *HelloWorld.runtimeconfig.json*

         Uygulamanın çalışma zamanı yapılandırma dosyası. Uygulamanızı çalıştırmak için oluşturulan .NET Core sürümünü tanımlar. Daha fazla bilgi için bkz: [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Yayımlanmış dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/publishedfiles.png)

Yayımlama işlemi yayımlanan uygulama sistemde yüklü .NET Core ile .NET Core tarafından desteklenen herhangi bir platformda çalıştırılacağı dağıtım türü olan bir framework bağımlı dağıtım oluşturur. Kullanıcılar, uygulamanızın vererek çalıştırabilirsiniz `dotnet HelloWorld.dll` bir konsol penceresinden komutu.

Yayımlama ve .NET Core uygulamaları dağıtma hakkında daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../../core/deploying/index.md).

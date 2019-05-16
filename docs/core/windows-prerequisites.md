---
title: Windows üzerinde .NET Core önkoşulları
description: Windows üzerinde gereken bağımlılıklar geliştirin ve .NET Core uygulamaları çalıştırmak için makine öğrenin.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 8eb2913b0fa1fe037a460633064d6f179b64a248
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634085"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows üzerinde .NET Core önkoşulları

Bu makalede, Windows üzerinde .NET Core uygulamaları çalıştırmak için desteklenen işletim sistemi sürümleri gösterilir. Windows üzerinde .NET Core uygulamaları geliştirme kullandığı üç yöntem desteklenen işletim sistemi sürümleri ve aşağıdaki bağımlılıkları geçerlidir:

* [Komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

Ayrıca, Visual Studio 2017 kullanarak Windows üzerinde geliştirme yapıyorsanız [Önkoşullar Visual Studio 2017 ile](#prerequisites-with-visual-studio-2017) bölüm gelecek .NET Core geliştirme için desteklenen en düşük sürümlerle ilgili daha ayrıntılı.

## <a name="net-core-supported-windows-versions"></a>.NET core desteklenen Windows sürümleri

.NET core üzerinde aşağıdaki sürümleri desteklenir:

* Windows 7 SP1
* Windows 8.1
* Windows 10 Yıldönümü Güncelleştirmesi (sürüm 1607) veya sonraki sürümler
* Windows Server 2008 R2 SP1 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2012 SP1 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2012 R2 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2016 veya sonraki sürümleri (tam sunucu, Sunucu Çekirdeği veya Nano Server)

## <a name="net-core-supported-operating-systems"></a>.NET core tarafından desteklenen işletim sistemleri

Aşağıdaki makaleler sürüm başına .NET Core desteklenen işletim sistemlerinin tam bir listesi vardır:

* [.NET core 3.0 (Önizleme)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

İndirme bağlantıları ve daha fazla bilgi için bkz: [.NET indirir](https://dotnet.microsoft.com/download) en son sürümü indirmek için veya [.NET arşiv indirir](https://dotnet.microsoft.com/download/archives#dotnet-core) eski sürümler için.

## <a name="net-core-dependencies"></a>.NET core bağımlılıkları

.NET core 1.1 ve önceki sürümlerinde Visual C++ yeniden dağıtılabilir Windows 10 ve Windows Server 2016'dan önceki Windows sürümlerinde çalışan gerektirir. Bu bağımlılık, .NET Core yükleyici tarafından otomatik olarak yüklenir.

[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) zaman el ile yüklenmelidir:

* .NET Core ile yükleme [yükleyicisi betiği](./tools/dotnet-install-script.md).
* Kendi başına bir .NET Core uygulaması dağıtma.
* Kaynak Ürün oluşturma.
* .NET Core ile yükleme bir *.zip* dosya. Bu derleme/CI/CD sunucuları ekleyebilirsiniz.

> [!NOTE]
> **Windows 8.1 ve önceki sürümleri veya Windows Server 2012 R2 ve önceki sürümleri için:**
>
> Windows yüklemenizin güncel olduğundan ve içerir emin [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), Windows güncelleştirmesi yüklenebilir. Bu yazılımın yüklü yoksa, .NET Core uygulamasını başlattığında aşağıdaki gibi bir hata görürsünüz: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Windows 7 veya Windows Server 2008 R2 için:**
>
> KB2999226 yanı sıra, ayrıca olduğundan emin olun [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) yüklü. Bu yazılımın yüklü yoksa, .NET Core uygulamasını başlattığında aşağıdakine benzer bir hata görürsünüz: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-for-net-core-30-preview-3"></a>.NET Core 3.0 Preview 3 için Önkoşullar

.NET core 3.0 Preview 3 olarak .NET Core diğer sürümleri aynı önkoşulları vardır. Ancak, Visual Studio kullanmak istiyorsanız projesi .NET Core 3.0 oluşturmak üzere, kullanmalısınız [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Visual Studio 2019 yüklü yan yana çakışma olmadan Visual Studio'nun diğer sürümleriyle birlikte olabilir.

## <a name="prerequisites-with-visual-studio-2017"></a>Visual Studio 2017 ile önkoşulları
    
.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz. Visual Studio 2017, Windows üzerinde .NET Core uygulamaları için bir tümleşik geliştirme ortamı sağlar.

Daha fazla Visual Studio 2017'deki değişiklikler hakkında [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.2 SDK'sını kullanarak Visual Studio 2017'de .NET Core uygulamaları geliştirmek için:

 1. [Visual Studio 2017 sürüm 15.9.0 yükleyip veya üzeri](/visualstudio/install/install-visual-studio) ile **.NET Core çoklu platform geliştirme** iş yükü (içinde **diğer araç takımları** bölümü) seçili.

![Seçili ".NET Core çoklu platform geliştirme" iş yüküyle Visual Studio 2017 ekran görüntüsü yükleme](./media/windows-prerequisites/vs-2017-workloads.jpg)

Sonra **.NET Core çoklu platform geliştirme** araç yüklendiğinde, Visual Studio, genellikle .NET Core SDK'ın önceki bir sürümünü yükler.
Örneğin, iş yükü yüklendikten sonra Visual Studio 2017 15.9 varsayılan olarak .NET Core 2.1 SDK'sını kullanır.

.NET Core 2.2 SDK'sını kullanmak için Visual Studio'yu güncelleştirmek için:

 1. Yükleme [.NET Core SDK'sını 2.2](https://dotnet.microsoft.com/download).

 1. En son .NET Core çalışma zamanı kullanmak için projenizin istiyorsanız aşağıdaki yönergeleri kullanarak .NET Core 2.2 için mevcut veya yeni .NET Core projeleri yeniden hedefle:

    * Üzerinde **proje** menüsünde seçin **özellikleri**.
    * İçinde **hedef Framework'ü** seçim menüsünde ayarlayın değeri **.NET Core 2.2**.

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle seçili öğe ".NET Core 2.2" hedef framework menüsü](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Visual Studio ile .NET Core 2.2 SDK yapılandırılmış oluşturduktan sonra aşağıdaki işlemleri yapabilirsiniz:

* Açın, derleme ve mevcut .NET Core 1.x ve 2.x'i projeleri çalıştırın.
* .NET Core 2.2, derleme, .NET Core 1.x ve 2.x'i projeleri yeniden hedefle ve çalıştırın.
* Yeni .NET Core 2.2 projeleri oluşturun.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

Visual Studio'da .NET Core 1.x uygulamalar geliştirmek için [Visual Studio 2017'yi indirip](/visualstudio/install/install-visual-studio) ile **".NET Core çoklu platform geliştirme"** iş yükü (içinde **diğer araç takımları**bölümü) seçili.

![Seçili ".NET Core çoklu platform geliştirme" iş yüküyle Visual Studio 2017 ekran görüntüsü yükleme](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> Visual Studio 2015 için .NET Core 1.x geliştirme kullanmak da mümkündür, ancak aşağıdaki nedenlerle önerilmez:
  > * .NET Core araçları, desteklenmeyen bir önizleme sürümüdür.
  > * Projeleri project.json tabanlı, kullanım dışı bırakılmıştır.
>
> Proje biçimi değişiklikler hakkında daha fazla bilgi için bkz. [değişiklikleri üst düzey genel bakış](./tools/cli-msbuild-architecture.md).

---

<a name="vs-mapping"></a>

> [!TIP]
> Visual Studio sürümünüz doğrulamak için:
>
> * Üzerinde **yardımcı** menüsünde seçin **Microsoft Visual Studio hakkında**.
> * İçinde **Microsoft Visual Studio hakkında** iletişim kutusunda, sürüm numarasını doğrulayın.
>   * .NET Core 3.0 Preview 3 uygulamaları için Visual Studio 2019 16,0 veya üzeri sürümler.
>   * .NET Core 2.2 uygulamaları için Visual Studio 2017 sürüm 15,9 veya üzeri.
>   * .NET Core 2.1 uygulamaları için Visual Studio 2017 sürüm 15.7 veya üzeri.
>   * .NET Core 1.x uygulamaları için Visual Studio 2017 sürüm 15.0 veya üzeri.

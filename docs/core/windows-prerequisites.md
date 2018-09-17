---
title: Windows üzerinde .NET Core önkoşulları
description: Windows üzerinde gereken bağımlılıklar geliştirin ve .NET Core uygulamaları çalıştırmak için makine öğrenin.
author: mairaw
ms.author: mairaw
ms.date: 08/31/2018
ms.openlocfilehash: 63c0de2b413f38458dba89506f4070760b3f53f8
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45747474"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows üzerinde .NET Core önkoşulları

Bu makalede, Windows üzerinde .NET Core uygulamaları geliştirmek için ihtiyaç duyulan bağımlılıkları gösterir. Windows üzerinde .NET Core uygulamaları geliştirme kullandığı üç yöntem desteklenen işletim sistemi sürümleri ve aşağıdaki bağımlılıkları geçerlidir:

* [Komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>.NET core desteklenen Windows sürümleri

.NET core üzerinde aşağıdaki sürümleri desteklenir:

* Windows 7 SP1
* Windows 8.1
* Windows 10 Yıldönümü Güncelleştirmesi (sürüm 1607) veya sonraki sürümler
* Windows Server 2008 R2 SP1 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2012 SP1 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2012 R2 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2016 veya sonraki sürümleri (tam sunucu, Sunucu Çekirdeği veya Nano Server)

## <a name="net-core-supported-operating-systems"></a>.NET core tarafından desteklenen işletim sistemleri

Aşağıdaki makaleler sürüm başına .NET Core desteklenen işletim sistemlerinin tam bir listesi vardır:

* [.NET core 2.1 - desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET core 2.0 - desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [.NET core 1.x - desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

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

## <a name="prerequisites-with-visual-studio-2017"></a>Visual Studio 2017 ile önkoşulları

.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz. Visual Studio 2017, Windows üzerinde .NET Core uygulamaları için bir tümleşik geliştirme ortamı sağlar.

Daha fazla Visual Studio 2017'deki değişiklikler hakkında [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

Visual Studio 2017'de .NET Core 2.1 uygulamaları geliştirmek için:

 1. [Visual Studio 2017 sürüm 15.7.0 yükleyip veya üzeri](/visualstudio/install/install-visual-studio) ile **.NET Core çoklu platform geliştirme** iş yükü (içinde **diğer araç takımları** bölümü) seçili.

![Seçili ".NET Core çoklu platform geliştirme" iş yüküyle Visual Studio 2017 ekran görüntüsü yükleme](./media/windows-prerequisites/vs-15-8-workloads.jpg)

Sonra **.NET Core çoklu platform geliştirme** araç takımı, varsayılan olarak yüklenir, Visual Studio 2017 15.7 kullanan .NET Core 2.0 SDK'sını ve Visual Studio 2017 15,8 2.1 SDK'sını kullanır.

 2. Visual Studio 2017 15.7 kullanıyorsanız yükleyin [.NET Core 2.1 SDK](https://www.microsoft.com/net/download/core) veya Visual Studio 2017 15,8 yükseltin.

 3. Aşağıdaki yönergeleri kullanarak .NET Core 2.1 için mevcut veya yeni .NET Core projeleri yeniden hedefle:
    * Üzerinde **proje** menüsünde Seç **özellikleri**.
    * İçinde **hedef Framework'ü** seçim menüsünde ayarlayın değeri **.NET Core 2.1**.

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle seçili öğe ".NET Core 2.0" hedef framework menüsü](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Visual Studio ile .NET Core 2.1 SDK yapılandırılmış oluşturduktan sonra aşağıdaki işlemleri yapabilirsiniz:

* Açın, derleme ve mevcut .NET Core 1.x ve 2.x'i projeleri çalıştırın.
* .NET Core yeniden hedefle 1.x ve .NET Core 2.1 2.0 projeleri derlemek ve çalıştırmak.
* Yeni .NET Core 2.1 projeleri oluşturun.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

Visual Studio 2017'de .NET Core 2.0 uygulamaları geliştirmek için:

 1. [Visual Studio 2017 sürüm 15.3.0 yükleyip veya üzeri](/visualstudio/install/install-visual-studio) ile **.NET Core çoklu platform geliştirme** iş yükü (içinde **diğer araç takımları** bölümü) seçili.

![Seçili ".NET Core çoklu platform geliştirme" iş yüküyle Visual Studio 2017 ekran görüntüsü yükleme](./media/windows-prerequisites/vs-15-3-workloads.jpg)

Sonra **.NET Core çoklu platform geliştirme** araç yüklendiğinde, Visual Studio 2017, .NET Core kullanan 1.x varsayılan olarak. Visual Studio 2017'de .NET Core 2.0 desteği almak için .NET Core 2.0 SDK'sını yükleyin.

 2. Yükleme [.NET Core 2.0 SDK'sı](https://www.microsoft.com/net/download/dotnet-core/2.0).
 3. Aşağıdaki yönergeleri kullanarak .NET Core 2.0 için mevcut veya yeni .NET Core 1.x projeleri yeniden hedefle:
    * Üzerinde **proje** menüsünde Seç **özellikleri**.
    * İçinde **hedef Framework'ü** seçim menüsünde ayarlayın değeri **.NET Core 2.0**.

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle seçili öğe ".NET Core 2.0" hedef framework menüsü](./media/windows-prerequisites/Targeting-dotnetCore2.png)

.NET Core 2.0 SDK'yı yükledikten sonra Visual Studio 2017, .NET Core SDK 2.0 varsayılan olarak kullanır ve aşağıdaki eylemleri destekler:

* Açık, derleme ve mevcut .NET Core 1.x projelerini çalıştırmak.
* .NET Core 2.0, derleme, .NET Core 1.x projeleri yeniden hedefle ve çalıştırın.
* Yeni .NET Core 2.0 projeleri oluşturun.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

Visual Studio'da .NET Core 1.x uygulamalar geliştirmek için [Visual Studio 2017'yi indirip](/visualstudio/install/install-visual-studio) ile **".NET Core çoklu platform geliştirme"** iş yükü (içinde **diğer araç takımları**bölümü) seçili.

![Seçili ".NET Core çoklu platform geliştirme" iş yüküyle Visual Studio 2017 ekran görüntüsü yükleme](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> Visual Studio 2015 için .NET Core 1.x geliştirme kullanmak da mümkündür, ancak aşağıdaki nedenlerle önerilmez:
  > * .NET Core araçları, desteklenmeyen bir önizleme sürümüdür.
  > * Projeleri project.json tabanlı, kullanım dışı bırakılmıştır.
>
> Proje biçimi değişiklikler hakkında daha fazla bilgi için bkz. [değişiklikleri üst düzey genel bakış](./tools/cli-msbuild-architecture.md).
---

<a name="vs-mapping"></a>

> [!TIP]
> Visual Studio 2017 sürüm doğrulamak için:
>
> * Üzerinde **yardımcı** menüsünde seçin **Microsoft Visual Studio hakkında**.
> * İçinde **Microsoft Visual Studio hakkında** iletişim kutusunda, sürüm numarasını doğrulayın.
>   * .NET Core 2.2 Önizleme 1 uygulamalar için Visual Studio 2017 sürüm 15.9 (şu anda önizlemede) veya üzeri.
>   * .NET Core 2.1 uygulamaları için Visual Studio 2017 sürüm 15.7 veya üzeri.
>   * .NET Core 2.0 uygulamaları için Visual Studio 2017 sürüm 15.3 veya üzeri.
>   * .NET Core 1.x uygulamaları için Visual Studio 2017 sürüm 15.0 veya üzeri.

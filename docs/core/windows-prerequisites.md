---
title: .NET Core Windows için Önkoşullar
description: Windows üzerinde gereken bağımlılıkları geliştirmek ve .NET Core uygulamaları çalıştırmak için makine öğrenin.
author: JRAlexander
ms.author: johalex
ms.date: 05/18/2018
ms.openlocfilehash: 3d172c83f0a79744afbaeeff52d7fea62d9b98b6
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34311994"
---
# <a name="prerequisites-for-net-core-on-windows"></a>.NET Core Windows için Önkoşullar

Bu makalede Windows .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir. Desteklenen işletim sistemi sürümleri ve izleyin bağımlılıkları Windows .NET Core uygulamaları geliştirme üç yolu için geçerlidir:

* [Komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>.NET core desteklenen Windows sürümleri

.NET core üzerinde aşağıdaki sürümleri desteklenir:

* Windows 7 SP1
* Windows 8.1
* Windows 10 Anniversary güncelleştirme (sürüm 1607) veya sonraki sürümler
* Windows Server 2008 R2 SP1 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2012 SP1 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2012 R2 (tam sunucu veya Sunucu Çekirdeği)
* Windows Server 2016 veya sonraki sürümleri (tam sunucu, Sunucu Çekirdeği veya Nano Server)

Aşağıdaki makalelerde her sürümü .NET Core desteklenen işletim sistemlerinin tam bir listesi vardır:

* [.NET core 2.1 - desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET core 2.0 - desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [.NET core 1.x - desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a>.NET core bağımlılıkları

.NET core 1.1 ve önceki sürümlerinde Visual C++ yeniden dağıtılabilir Windows 10 ve Windows Server 2016'den önceki Windows sürümlerinde çalışan gerektirir. Bu bağımlılık .NET Core yükleyici tarafından otomatik olarak yüklenir.

[Microsoft Visual C++ 2015 Redistributable güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) zaman el ile yüklenmelidir:

* .NET Core ile yükleme [yükleyicisi betiği](./tools/dotnet-install-script.md).
* Bağımsız bir .NET Core uygulamasını dağıtma.
* Kaynak Ürün oluşturma.
* .NET Core yoluyla yükleme bir *.zip* dosyası. Bu yapı/CI/CD sunucuları içerebilir.

> [!NOTE]
> **Windows 8.1 ve önceki sürümleri veya Windows Server 2012 R2 ve önceki sürümleri için:**
>
> Windows yüklemenizi güncel olduğundan ve içerir emin olun [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), yüklenebileceği Windows Update aracılığıyla. Bu güncelleştirmenin yüklü yoksa, .NET Core uygulama başlattığında aşağıdaki gibi bir hata görürsünüz: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Windows 7 veya Windows Server 2008 R2 için:**
>
> KB2999226 ek olarak, aynı zamanda sahip olduğunuzdan emin olun [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) yüklü. Bu güncelleştirmenin yüklü yoksa, bir .NET Core uygulamasını başlattığında aşağıdakine benzer bir hata görürsünüz: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-with-visual-studio-2017"></a>Visual Studio 2017 önkoşulları

.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir Düzenleyicisi'ni kullanabilirsiniz. [Visual Studio 2017](#visual-studio-2017) Windows .NET Core uygulamaları için bir tümleşik geliştirme ortamı sağlar.

Daha fazla bilgiyi Visual Studio 2017'deki değişiklikler hakkında [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

Visual Studio 2017 .NET Core 2.x uygulamaları geliştirmek için:

 1. [Visual Studio 2017 15.3.0 sürümünü karşıdan yükleyip ya da daha yüksek](/visualstudio/install/install-visual-studio) ile **.NET Core platformlar arası geliştirme** iş yükü (içinde **diğer Toolsets** bölüm) seçili.

![Seçili ".NET Core platformlar arası geliştirme" iş yükü ile Visual Studio 2017 ekran yükleme](./media/windows-prerequisites/vs-15-3-workloads.jpg)

Sonra **.NET Core platformlar arası geliştirme** araç takımı yüklendiğinde, Visual Studio 2017 kullanan .NET Core 1.x varsayılan olarak. .NET Core yükleme 2.x SDK Visual Studio 2017 .NET Core 2.x destek alma.

 2. Yükleme [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).
 3. .NET Core mevcut veya yeni .NET Core 1.x projelerine yeniden hedefleyin 2.x aşağıdaki yönergeleri kullanarak:
    * Üzerinde **proje** menüsünde Seç **özellikleri**.
    * İçinde **hedef framework** seçim menüsünü kümesine değeri **.NET Core 2.0**.

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle öğesinin seçili ".NET Core 2.0" hedef framework menüsü](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Bir kez .NET Core 2.x SDK yüklü Visual Studio 2017 kullanan .NET Core SDK 2.x varsayılan ve aşağıdaki eylemleri destekler:

* Açın, yapı ve mevcut .NET Core 1.x projeleri çalıştırın.
* .NET Core 1.x projeleri .NET Core 2.x, derleme ve çalıştırma yeniden hedefleyin.
* Yeni .NET Core 2.x projeler oluşturun.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

Visual Studio'da .NET Core 1.x uygulamaları geliştirmek için [yükleyip Visual Studio 2017 RTM (sürüm 15.0.26228.4) ya da daha yüksek](/visualstudio/install/install-visual-studio) ile **".NET Core platformlar arası geliştirme"** iş yükündeki (  **Diğer Toolsets** bölüm) seçili.

![Seçili ".NET Core platformlar arası geliştirme" iş yükü ile Visual Studio 2017 ekran yükleme](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> .NET Core 1.x geliştirme için Visual Studio 2015 kullanmak da mümkündür, ancak aşağıdaki nedenlerden dolayı önerilmez:
  > * .NET Core araç desteklenmeyen bir önizleme sürümüdür.
  > * Projeleri project.json tabanlı, kullanım dışı bırakılmıştır.
>
> Proje biçimi değişiklikler hakkında daha fazla bilgi için bkz: [değişiklikleri üst düzey genel bakış](./tools/cli-msbuild-architecture.md).
---

> [!TIP]
> Visual Studio 2017 sürümünüzü doğrulamak için:
>
> * Üzerinde **yardımcı** menüsünde seçin **Microsoft Visual Studio hakkında**.
> * İçinde **Microsoft Visual Studio hakkında** iletişim kutusunda, sürüm numarasını doğrulayın.
>   * .NET Core 2.1 RC uygulamalar için Visual Studio 2017 15.7 veya daha yüksek bir sürümü.
>   * .NET Core 2.0 uygulamalar için Visual Studio 2017 15.3 veya daha yüksek bir sürümü.
>   * .NET Core 1.x uygulamalar için Visual Studio 2017 15.0 veya daha yüksek bir sürümü.

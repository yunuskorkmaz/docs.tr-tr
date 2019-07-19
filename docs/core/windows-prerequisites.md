---
title: Windows üzerinde .NET Core önkoşulları
description: .NET Core uygulamaları geliştirmek ve çalıştırmak için Windows makinenizde hangi bağımlılıklara ihtiyacınız olduğunu öğrenin.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 1921ef565c2d04624009f7684e439ddba1cdf57e
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331067"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows üzerinde .NET Core önkoşulları

Bu makalede, Windows 'da .NET Core uygulamalarını çalıştırmak için desteklenen işletim sistemi sürümleri gösterilmektedir. Desteklenen işletim sistemi sürümleri ve aşağıdaki bağımlılıklar, Windows 'ta .NET Core uygulamaları geliştirmenin üç yolu için geçerlidir:

* [Komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

Ayrıca, Visual Studio 2017 kullanarak Windows üzerinde geliştirme yapıyorsanız, [Visual studio 2017 Ile Önkoşullar](#prerequisites-with-visual-studio-2017) bölümü, .NET Core geliştirmesi için desteklenen en düşük sürümler hakkında daha ayrıntılı bilgi alır.

## <a name="net-core-supported-operating-systems"></a>.NET Core tarafından desteklenen işletim sistemleri

Aşağıdaki makalelerde sürüm başına .NET Core tarafından desteklenen işletim sistemlerinin kapsamlı bir listesi verilmiştir:

* [.NET Core 3,0 (Önizleme)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET Core 1,0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

İndirme bağlantıları ve daha fazla bilgi için bkz. eski sürümler için en son sürümü veya [.net İndirmeleri arşivini](https://dotnet.microsoft.com/download/archives#dotnet-core) indirmek üzere [.net İndirmeleri](https://dotnet.microsoft.com/download) .

## <a name="net-core-dependencies"></a>.NET Core bağımlılıkları

.NET Core 1,1 ve önceki sürümleri, Windows 10 C++ ve windows Server 2016 ' den önceki Windows sürümlerinde çalışırken görsel yeniden dağıtılabilir gerektirir. Bu bağımlılık, .NET Core yükleyicisi tarafından otomatik olarak yüklenir.

[Microsoft Visual C++ 2015 Redistributable güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) , şu durumlarda el ile yüklenmelidir:

* .NET Core, [Yükleyici betiği](./tools/dotnet-install-script.md)ile yükleniyor.
* Kendi kendine içerilen bir .NET Core uygulaması dağıtma.
* Ürünün kaynaktan oluşturulması.
* .NET Core 'u bir *. zip* dosyası aracılığıyla yükleme. Bu, derleme/CI/CD sunucuları içerebilir.

> [!NOTE]
> **Windows 8.1 ve önceki sürümler veya Windows Server 2012 R2 ve önceki sürümleri için:**
>
> Windows yüklemenizin güncel olduğundan ve Windows Update aracılığıyla yüklenebilen [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows)içerdiğinden emin olun. Bu güncelleştirme yüklü değilse, bir .NET Core uygulaması başlattığınızda aşağıdakine benzer bir hata görürsünüz:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Windows 7 veya Windows Server 2008 R2 için:**
>
> KB2999226 ' ye ek olarak, [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) ' ın de yüklü olduğundan emin olun. Bu güncelleştirme yüklü değilse, bir .NET Core uygulaması başlattığınızda aşağıdakine benzer bir hata görürsünüz: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-for-net-core-30-preview-3"></a>.NET Core 3,0 Preview 3 önkoşulları

.NET Core 3,0 Preview 3, diğer .NET Core sürümleriyle aynı önkoşullara sahiptir. Ancak, .NET Core 3,0 projeleri oluşturmak için Visual Studio 'Yu kullanmak istiyorsanız, [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)' i kullanmanız gerekir. Visual Studio 2019, çakışma olmadan Visual Studio 'nun diğer sürümleriyle yan yana yüklenebilir.

## <a name="prerequisites-with-visual-studio-2017"></a>Visual Studio 2017 ile Önkoşullar
    
.NET Core SDK kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz. Visual Studio 2017, Windows üzerinde .NET Core uygulamaları için tümleşik bir geliştirme ortamı sağlar.

Visual Studio 2017 ' deki değişiklikler hakkında daha fazla bilgi için bkz. [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

.NET Core 2,2 SDK kullanarak Visual Studio 2017 ' de .NET Core uygulamaları geliştirmek için:

 1. **.NET Core platformlar arası geliştirme** iş yükü ( **diğer araç kümeleri** bölümünde) seçiliyken [Visual Studio 2017 sürüm 15.9.0 veya üstünü indirip yükleyin](/visualstudio/install/install-visual-studio) .

![".NET Core platformlar arası geliştirme" iş yükü seçiliyken Visual Studio 2017 yüklemesinin ekran görüntüsü](./media/windows-prerequisites/vs-2017-workloads.jpg)

**.NET Core platformlar arası geliştirme** araç takımı yüklendikten sonra, Visual Studio genellikle .NET Core SDK önceki bir sürümünü yüklüyor.
Örneğin, Visual Studio 2017 15,9, iş yükü yüklendikten sonra varsayılan olarak .NET Core 2,1 SDK kullanır.

Visual Studio 'Yu .NET Core 2,2 SDK kullanacak şekilde güncelleştirmek için:

 1. [.NET Core 2,2 SDK 'sını](https://dotnet.microsoft.com/download)yükler.

 1. Projenizin en son .NET Core çalışma zamanını kullanmasını istiyorsanız, aşağıdaki yönergeleri kullanarak var olan veya yeni .NET Core projelerini .NET Core 2,2 'e yeniden hedefleyin:

    * **Proje** menüsünde **Özellikler**' i seçin.
    * **Hedef çerçeve** seçim menüsünde, değeri **.NET Core 2,2**olarak ayarlayın.

![Visual Studio 2017 uygulama projesi özelliğinin ".NET Core 2,2" hedef Framework menü öğesi seçiliyken ekran görüntüsü](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Visual Studio 'Yu .NET Core 2,2 SDK ile yapılandırdıktan sonra, aşağıdaki işlemleri yapabilirsiniz:

* Mevcut .NET Core 1. x ve 2. x projelerini açın, derleyin ve çalıştırın.
* .NET Core 1. x ve 2. x projelerini .NET Core 2,2, derlemek ve çalıştırmak için yeniden hedefleyin.
* Yeni .NET Core 2,2 projeleri oluşturun.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

Visual Studio 'da .NET Core 1. x uygulamaları geliştirmek için, [Visual studio 2017](/visualstudio/install/install-visual-studio) ' i **".NET Core platformlar arası geliştirme"** Iş yükü ( **diğer araç kümeleri** bölümünde) seçili olacak şekilde indirip yükleyin.

![".NET Core platformlar arası geliştirme" iş yükü seçiliyken Visual Studio 2017 yüklemesinin ekran görüntüsü](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> .NET Core 1. x geliştirme için Visual Studio 2015 kullanmak mümkündür, ancak aşağıdaki nedenlerden dolayı önerilmez:
  > * .NET Core araçları, desteklenmeyen bir önizleme sürümüdür.
  > * Projeler, kullanım dışı olan Project. JSON tabanlıdır.
>
> Proje biçimi değişiklikleri hakkında daha fazla bilgi için bkz. [değişikliklere Ilişkin üst düzey genel bakış](./tools/cli-msbuild-architecture.md).

---

<a name="vs-mapping"></a>

> [!TIP]
> Visual Studio sürümünüzü doğrulamak için:
>
> * **Yardım** menüsünde **Microsoft Visual Studio hakkında**' yı seçin.
> * **Microsoft Visual Studio hakkında** iletişim kutusunda sürüm numarasını doğrulayın.
>   * .NET Core 3,0 Preview 3 uygulamaları, Visual Studio 2019 sürüm 16,0 veya üzeri için.
>   * .NET Core 2,2 uygulamaları için Visual Studio 2017 sürüm 15,9 veya üzeri.
>   * .NET Core 2,1 uygulamaları için Visual Studio 2017 sürüm 15,7 veya üzeri.
>   * .NET Core 1. x uygulamaları, Visual Studio 2017 sürüm 15,0 veya üzeri için.

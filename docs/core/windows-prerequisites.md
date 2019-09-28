---
title: Windows üzerinde .NET Core önkoşulları
description: .NET Core uygulamaları geliştirmek ve çalıştırmak için Windows makinenizde hangi bağımlılıklara ihtiyacınız olduğunu öğrenin.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: b1557e6910cb6d0b6d7e2b3ce2aec97d3715fec7
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591665"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows üzerinde .NET Core önkoşulları

Bu makalede, Windows 'da .NET Core uygulamalarını çalıştırmak için desteklenen işletim sistemi sürümleri gösterilmektedir. Desteklenen işletim sistemi sürümleri ve aşağıdaki bağımlılıklar, Windows 'ta .NET Core uygulamaları geliştirmenin üç yolu için geçerlidir:

* [Komut satırı](./tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [Visual Studio Code](https://code.visualstudio.com/)

Ayrıca, Visual Studio 'Yu kullanarak Windows üzerinde geliştirirseniz, [Visual Studio ile .NET Core uygulamaları geliştirmeye yönelik önkoşullar](#prerequisites-to-develop-net-core-apps-with-visual-studio) , .NET Core geliştirmesi için desteklenen en düşük sürümler hakkında daha ayrıntılı bilgi sağlar.

## <a name="net-core-supported-operating-systems"></a>.NET Core tarafından desteklenen işletim sistemleri

Aşağıdaki makalelerde sürüm başına .NET Core tarafından desteklenen işletim sistemlerinin kapsamlı bir listesi verilmiştir:

* [.NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

İndirme bağlantıları ve daha fazla bilgi için bkz. eski sürümler için en son sürümü veya [.net İndirmeleri arşivini](https://dotnet.microsoft.com/download/archives#dotnet-core) indirmek üzere [.net İndirmeleri](https://dotnet.microsoft.com/download) .

## <a name="net-core-dependencies"></a>.NET Core bağımlılıkları

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

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a>Visual Studio ile .NET Core uygulamaları geliştirmeye yönelik önkoşullar
    
.NET Core SDK kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz, ancak Visual Studio 2017 ve üzeri sürümleri, Windows üzerinde .NET Core uygulamaları için tümleşik bir geliştirme ortamı sağlar.

<a name="vs-mapping"></a>

Her .NET Core sürümünde en düşük Visual Studio sürümü gerekir. Visual Studio sürümünüzü doğrulamak için:

* **Yardım** menüsünde **Microsoft Visual Studio hakkında**' yı seçin.
* **Microsoft Visual Studio hakkında** iletişim kutusunda sürüm numarasını doğrulayın.

Aşağıdaki tabloda her SDK için en düşük sürüm listelenmektedir:

| .NET Core SDK sürümü | Visual Studio sürümü                      |
| --------------------- | ------------------------------------------ |
| 3,0                   | Visual Studio 2019 sürüm 16,3 veya üzeri. |
| 2.2                   | Visual Studio 2017 sürüm 15,9 veya üzeri. |
| 2.1                   | Visual Studio 2017 sürüm 15,7 veya üzeri. |
| 'in                   | Visual Studio 2017 sürüm 15,0 veya üzeri. |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0 SDK kullanarak Visual Studio 2019 ' de .NET Core uygulamaları geliştirmek için:

* [Visual Studio 2019 sürüm 16,3 veya üstünü indirip yükleyin](/visualstudio/install/install-visual-studio) ve oluşturmakta olduğunuz uygulamanın türüne bağlı olarak .NET Core SDK içeren aşağıdaki iş yüklerinden birini seçin:

  * **Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.
  * **Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.
  * **Windows** bölümündeki **net masaüstü geliştirme** iş yükü.

Aşağıdaki görüntüde, Visual Studio Kullanıcı arabiriminde seçilen **.NET Core platformlar arası geliştirme** iş yükü gösterilmektedir:

![".NET Core platformlar arası geliştirme" iş yükü seçiliyken Visual Studio 2019 yüklemesinin ekran görüntüsü](./media/windows-prerequisites/vs-2019-workloads.jpg)

Visual Studio 2019 16,3, bu iş yüklerinden herhangi biri yüklendikten sonra varsayılan olarak .NET Core 3,0 SDK kullanır.

Mevcut projelerinizin en son .NET Core çalışma zamanını kullanmasını istiyorsanız, aşağıdaki yönergeleri kullanarak var olan tüm .NET Core projelerini .NET Core 3,0 ' e yeniden hedefleyin:

* **Proje** menüsünde **Özellikler**' i seçin.
* **Hedef çerçeve** seçim menüsünde, değeri **.NET Core 3,0**olarak ayarlayın.

![Visual Studio 2019 uygulama projesi özelliğinin ".NET Core 3,0" hedef Framework menü öğesi seçiliyken ekran görüntüsü](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

Visual Studio 'Yu .NET Core 3,0 SDK ile yapılandırdıktan sonra, aşağıdaki işlemleri yapabilirsiniz:

* Mevcut .NET Core 1. x ve 2. x projelerini açın, derleyin ve çalıştırın.
* .NET Core 1. x ve 2. x projelerini .NET Core 3,0, derlemek ve çalıştırmak için yeniden hedefleyin.
* Yeni .NET Core 3,0 projeleri oluşturun.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

.NET Core 2,2 SDK kullanarak Visual Studio 2017 ' de .NET Core uygulamaları geliştirmek için:

* **.NET Core platformlar arası geliştirme** iş yükü ( **diğer araç kümeleri** bölümünde) seçiliyken [Visual Studio 2019 sürüm 16,3 veya üstünü indirip yükleyin](/visualstudio/install/install-visual-studio) .
* **.NET Core platformlar arası geliştirme** iş yükü ( **diğer araç kümeleri** bölümünde) seçiliyken [Visual Studio 2017 sürüm 15.9.0 veya üstünü indirip yükleyin](/visualstudio/install/install-visual-studio) .

![".NET Core platformlar arası geliştirme" iş yükü seçiliyken Visual Studio 2017 yüklemesinin ekran görüntüsü](./media/windows-prerequisites/vs-2017-workloads.jpg)

**.NET Core platformlar arası geliştirme** araç takımı yüklendikten sonra, Visual Studio genellikle .NET Core SDK önceki bir sürümünü yüklüyor.
Örneğin, Visual Studio 2017 15,9, iş yükü yüklendikten sonra varsayılan olarak .NET Core 2,1 SDK kullanır.

Visual Studio 'Yu .NET Core 2,2 SDK kullanacak şekilde güncelleştirmek için:

 1. [.NET Core 2,2 SDK 'sını](https://dotnet.microsoft.com/download)yükler.

 1. Projenizin en son .NET Core çalışma zamanını kullanmasını istiyorsanız, aşağıdaki yönergeleri kullanarak, mevcut veya yeni .NET Core projelerini .NET Core 2,2 'e yeniden hedefleyin:

    * **Proje** menüsünde **Özellikler**' i seçin.
    * **Hedef çerçeve** seçim menüsünde, değeri **.NET Core 2,2**olarak ayarlayın.

![Visual Studio 2017 uygulama projesi özelliğinin ".NET Core 2,2" hedef Framework menü öğesi seçiliyken ekran görüntüsü](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Visual Studio 'Yu .NET Core 2,2 SDK ile yapılandırdıktan sonra, aşağıdaki işlemleri yapabilirsiniz:

* Mevcut .NET Core 1. x ve 2. x projelerini açın, derleyin ve çalıştırın.
* .NET Core 1. x ve 2. x projelerini .NET Core 2,2, derlemek ve çalıştırmak için yeniden hedefleyin.
* Yeni .NET Core 2,2 projeleri oluşturun.

---

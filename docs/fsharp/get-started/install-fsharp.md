---
title: F# yükleme
description: Ortamınıza göre yüklemeyi F# öğrenin.
ms.date: 09/05/2019
ms.openlocfilehash: 18b660ff640904119d63f57405752a14f7673e0c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400727"
---
# <a name="install-f"></a>F 'yi yükler\#

Ortamınıza bağlı olarak F# birden çok şekilde yükleyebilirsiniz.

## <a name="install-f-with-visual-studio"></a>Visual F# Studio ile Install

[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ilk kez indiriyorsanız, Ilk olarak Visual Studio yükleyicisi 'ni yükler. Yükleyiciden uygun Visual Studio SKU 'sunu yükleme. Zaten yüklüyse **Değiştir**' e tıklayın.

Daha sonra Iş yüklerinin bir listesini görürsünüz. ASP.NET Core projelerine yönelik destek ve .NET Core desteğini F# yükleyecek **ASP.net ve Web geliştirme '** yi seçin.

Sonra sağ alt taraftaki **Değiştir** ' e tıklayın.  Bu işlem, seçtiğiniz her şeyi yükler. Ardından Başlat ' a tıklayarak Visual Studio 2017 F# ' i dil desteğiyleaçabilirsiniz.

## <a name="install-f-with-visual-studio-for-mac"></a>Mac için Visual Studio F# ile yüklensin

F#, seçtiğiniz yapılandırma bağımsız olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)varsayılan olarak yüklenir.

Yüklemesi tamamlandıktan sonra, "Visual Studio 'Yu Başlat" ı seçin. MacOS 'ta Finder aracılığıyla da başlatabilirsiniz.

## <a name="install-f-with-visual-studio-code"></a>Visual Studio Code F# ile yüklensin

Proje şablonlarını kullanabilmeniz için, git ' in sizin YOLUNUZDA [yüklü](https://git-scm.com/download) ve kullanılabilir olması gerekir. Bir komut istemine yazıp `git --version` **ENTER**tuşuna basarak doğru şekilde yüklendiğini doğrulayabilirsiniz.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com) , [ F# etkileşimli](../tutorials/fsharp-interactive/index.md) destek için kullanılır. MacOS 'ta mono yüklemenin en kolay yolu homebrew aracılığıyla yapılır. Yalnızca aşağıdakileri terminalinize yazmanız yeterlidir:

```console
brew install mono
```

[.NET Core SDK](https://www.microsoft.com/net/download)de yükler.

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com) , [ F# etkileşimli](../tutorials/fsharp-interactive/index.md) destek için kullanılır. Decan veya Ubuntu kullanıyorsanız, aşağıdakileri kullanabilirsiniz:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

[.NET Core SDK](https://www.microsoft.com/net/download)de yükler.

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

[Visual Studio 'yu desteğiyle F# birlikte](#install-f-with-visual-studio)yüklersiniz. Bu, kod yazmak, derlemek ve yürütmek F# için gerekli tüm bileşenleri yüklüyor.

[.NET Core SDK](https://www.microsoft.com/net/download/)de yükler.

---

Daha sonra [Visual Studio Code](https://code.visualstudio.com) yüklenmesi gerekir.

Sonra, uzantılar simgesine tıklayın ve "ıonıde" araması yapın:

Visual Studio Code ' de destek için F# gereken tek eklenti [ıonıde-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)' dir. Ancak, [paket](https://fsprojects.github.io/Paket/) desteğini almak için [sahte](https://fsharp.github.io/FAKE/) destek ve [ıonıde-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) sağlamak üzere [ıonıde-sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) ' i de yükleyebilirsiniz. SAHTE ve paket, sırasıyla F# projeler oluşturmaya ve bağımlılıkları yönetmeye yönelik ek topluluk araçlarıdır.

## <a name="install-f-on-a-build-server"></a>Derleme F# sunucusuna yüklensin

.NET Core veya .NET SDK aracılığıyla .NET Framework kullanıyorsanız, derleme sunucunuza .NET SDK 'yı yüklemeniz yeterlidir. İhtiyacınız olan her şeye sahiptir.

.NET Framework kullanıyorsanız ve .NET **SDK kullanmıyorsanız,** [Visual Studio derleme araçları SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 'sunu Windows sunucunuza yüklemeniz gerekecektir. Yükleyicide, **.net masaüstü derleme araçları** ' nı seçin ve ardından yükleyici menüsünün sağ tarafındaki  **F# derleyici** bileşenini seçin.

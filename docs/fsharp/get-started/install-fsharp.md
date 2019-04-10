---
title: YüklemeF#
description: Yüklemeyi öğrenin F# ortamınıza bağlı.
ms.date: 08/28/2018
ms.openlocfilehash: 792c61c0522cd4d0c68a64572f2892ce33f71ea6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331981"
---
# <a name="install-f"></a>F yükleyin\#

Yükleyebileceğiniz F# ortamınıza bağlı olarak birden çok yolla.

## <a name="install-f-with-visual-studio"></a>Yükleme F# Visual Studio ile

Karşıdan yükleme, [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ilk kez, Visual Studio yükleyicisi ilk yükler. Uygun SKU, Visual Studio Yükleyicisi'nden yükleyin. Yüklü zaten varsa tıklayın **Değiştir**.

Sonraki iş yüklerinin bir listesini görürsünüz. Seçin **ASP.NET ve web geliştirme** hangi yükleme F# desteği ve .NET Core, ASP.NET Core projeleri için destek.

Ardından, **Değiştir** alt sağ tarafındaki.  Bu, seçtiğiniz her şeyi yükler. Daha sonra Visual Studio 2017 ile açabilirsiniz F# tıklayarak dil desteği **başlatma**.

## <a name="install-f-with-visual-studio-for-mac"></a>Yükleme F# Mac için Visual Studio ile

F#Varsayılan olarak yüklü [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), seçtiğiniz yapılandırma ne olursa olsun.

Yükleme tamamlandıktan sonra "Visual Studio Başlat"'i seçin. Ayrıca bu Bulucu Macos'ta başlatabilirsiniz.

## <a name="install-f-with-visual-studio-code"></a>Yükleme F# Visual Studio Code ile

Olması gerekir [yüklü git](https://git-scm.com/download) ve kullanılabilir hale getirmek için yol proje şablonlarını kullanın. Doğru yazarak yüklendiğinden emin olun `git --version` bir komut istemi ve tuşlarına basarak **Enter**.

### [<a name="macos"></a>macOS](#tab/macos)

[Mono](https://www.mono-project.com) için kullanılan [ F# etkileşimli](../tutorials/fsharp-interactive/index.md) destekler. Homebrew Macos'ta Mono yükleme için en kolay yoludur. Yalnızca, terminale aşağıdaki komutu yazın:

```console
brew install mono
```

Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download).

### [<a name="linux"></a>Linux](#tab/linux)

[Mono](https://www.mono-project.com) için kullanılan [ F# etkileşimli](../tutorials/fsharp-interactive/index.md) destekler. Debian veya Ubuntu'da üzerinde kullanıyorsanız aşağıdakileri kullanabilirsiniz:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download).

### [<a name="windows"></a>Windows](#tab/windows)

Yükleme [Visual Studio'yla F# Destek](#install-f-with-visual-studio). Bu yazma, derlemek ve çalıştırmak için gereken tüm bileşenleri yükler F# kod.

Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/).

---

Daha sonra ihtiyacınız olacak [Visual Studio Code](https://code.visualstudio.com) yüklü.

Ardından, "Ionide" için arama ve uzantıları simgesine tıklayın:

Yalnızca eklenti gereklidir F# desteği Visual Studio code'da [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Ancak, da yükleyebilirsiniz [Ionide sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) almak için [sahte](https://fsharp.github.io/FAKE/) desteklemek ve [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [Paket](https://fsprojects.github.io/Paket/) destekler. SAHTE ve Paket ek F# projeleri derleme ve bağımlılıkları, sırasıyla yönetmek için topluluk araçları.

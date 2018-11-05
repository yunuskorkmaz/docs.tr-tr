---
title: "F #'ı yükleme"
description: 'F # ortamınıza bağlı olarak yüklemeyi öğrenin.'
ms.date: 08/28/2018
ms.openlocfilehash: d53ecdcba5411db62208cb683a0fad795711b77c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50193909"
---
# <a name="install-f"></a>F #'ı yükleme #

F # birden çok yolla, ortamınıza bağlı olarak yükleyebilirsiniz.

## <a name="install-f-with-visual-studio"></a>F # ile Visual Studio'yu yükleyin

Karşıdan yükleme, [Visual Studio](https://visualstudio.microsoft.com/) ilk kez, Visual Studio yükleyicisi ilk yükler. Uygun SKU, Visual Studio Yükleyicisi'nden yükleyin. Yüklü zaten varsa tıklayın **Değiştir**.

Sonraki iş yüklerinin bir listesini görürsünüz. Seçin **ASP.NET ve web geliştirme** hangi yükler F # desteği ve ASP.NET Core projeleri için .NET Core desteği.

Ardından, **Değiştir** alt sağ tarafındaki.  Bu, seçtiğiniz her şeyi yükler. Ardından Visual Studio 2017 F # dil desteğiyle tıklayarak açabileceğiniz **başlatma**.

## <a name="install-f-with-visual-studio-for-mac"></a>F # Mac için Visual Studio ile yükleme

F # yüklendiğinde varsayılan olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/), seçtiğiniz yapılandırma ne olursa olsun.

Yükleme tamamlandıktan sonra "Visual Studio Başlat"'i seçin. Ayrıca bu Bulucu Macos'ta başlatabilirsiniz.

## <a name="install-f-with-visual-studio-code"></a>F # ile Visual Studio Code'u yükleyin

Olması gerekir [yüklü git](https://git-scm.com/download) ve kullanılabilir hale getirmek için yol proje şablonlarını kullanın. Doğru yazarak yüklendiğinden emin olun `git --version` bir komut istemi ve tuşlarına basarak **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com) için kullanılan [F # Etkileşimli](../tutorials/fsharp-interactive/index.md) destekler. Homebrew Macos'ta Mono yükleme için en kolay yoludur. Yalnızca, terminale aşağıdaki komutu yazın:

```console
brew install mono
```

Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com) için kullanılan [F # Etkileşimli](../tutorials/fsharp-interactive/index.md) destekler. Debian veya Ubuntu'da üzerinde kullanıyorsanız aşağıdakileri kullanabilirsiniz:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Yükleme [F # desteği ile Visual Studio](#install-f-with-visual-studio). Bu, yazma, derleme ve F # kodu yürütmek için gereken tüm bileşenleri yükler.

Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/).

---

Daha sonra ihtiyacınız olacak [Visual Studio Code](https://code.visualstudio.com) yüklü.

Ardından, "Ionide" için arama ve uzantıları simgesine tıklayın:

Visual Studio code'da F # desteği için gerekli yalnızca eklenti [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Ancak, da yükleyebilirsiniz [Ionide sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) almak için [sahte](https://fsharp.github.io/FAKE/) desteklemek ve [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [Paket](https://fsprojects.github.io/Paket/) destekler. SAHTE ve Paket projeleri derleme ve bağımlılıkları, sırasıyla yönetmek için ek F # topluluğu araçlar.

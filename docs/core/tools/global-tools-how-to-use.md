---
title: 'Öğretici: Bir .NET Core global aracı nı yükleyin ve kullanın'
description: Bir .NET aracını genel bir araç olarak nasıl yükleyip kullanacağınızı öğrenin.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156744"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

Bu öğretici, genel bir aracı nasıl yükleyip kullanacağınızı öğretir. [Bu serinin ilk öğretici](global-tools-how-to-create.md)oluşturduğunuz bir araç kullanın.

## <a name="prerequisites"></a>Önkoşullar

* Bu [serinin ilk öğretici](global-tools-how-to-create.md)tamamlayın.

## <a name="use-the-tool-as-a-global-tool"></a>Aracı genel bir araç olarak kullanma

1. *microsoft.botsay* proje klasöründe [dotnet aracı yükleme](dotnet-tool-install.md) komutunu çalıştırarak paketi paketten aracı yükleyin:

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   Parametre ,NET `--global` Core CLI'ye araç ikililerini PATH ortamı değişkenine otomatik olarak eklenen varsayılan bir konuma yüklemesini söyler.

   Parametre .NET `--add-source` Core CLI'ye *./nupkg* dizinini NuGet paketleri için ek kaynak akışı olarak geçici olarak kullanmasını söyler. Paketinize, paketinizin Nuget.org sitesinde değil, yalnızca *./nupkg* dizininde bulunduğundan emin olmak için benzersiz bir ad verdiniz.

   Çıktı, aracı çağırmak için kullanılan komutu ve yüklenen sürümü gösterir:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Aracı çağırın:

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Bu komut başarısız olursa, PATH'i yenilemek için yeni bir terminal açmanız gerekebilir.

1. [Dotnet aracını kaldır](dotnet-tool-uninstall.md) komutunu çalıştırarak aracı kaldırın:

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Aracı özel bir konuma yüklenen genel bir araç olarak kullanma

1. Paketi yükleyin.

   Windows'da:

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   Linux veya macOS'ta:

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   `--tool-path` Parametre .NET Core CLI'ye takım ikililerini belirtilen konuma yüklemesini söyler. Dizin yoksa oluşturulur. Bu dizin, PATH ortamı değişkenine otomatik olarak eklenmez.

   Çıktı, aracı çağırmak için kullanılan komutu ve yüklenen sürümü gösterir:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Aracı çağırın:

   Windows'da:

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   Linux veya macOS'ta:

   ```console
   ~/bin/botsay hello from the bot
   ```

1. [Dotnet aracını kaldır](dotnet-tool-uninstall.md) komutunu çalıştırarak aracı kaldırın:

   Windows'da:

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   Linux veya macOS'ta:

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>Sorun giderme

Öğreticiyi izlerken bir hata iletisi alırsanız, [Sorun Giderme .NET Core araç kullanım sorunlarına](troubleshoot-usage-issues.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir aracı genel bir araç olarak yüklemiş ve kullanmışsınız. Yerel bir araçla aynı aracı yüklemek ve kullanmak için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Yerel araçları yükleme ve kullanma](local-tools-how-to-use.md)

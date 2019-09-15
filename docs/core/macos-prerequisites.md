---
title: Mac üzerinde .NET Core önkoşulları
description: MacOS makinelerinde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen macOS sürümleri ve .NET Core bağımlılıkları.
author: mairaw
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 07/13/2019
ms.openlocfilehash: d391c18a371d721419c298f2987894f16ecbd169
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969920"
---
# <a name="prerequisites-for-net-core-on-macos"></a>MacOS 'ta .NET Core önkoşulları

Bu makalede, macOS makinelerinde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için ihtiyacınız olan desteklenen macOS sürümleri ve .NET Core bağımlılıkları gösterilmektedir. Desteklenen işletim sistemi sürümleri ve bağımlılıklar, bir Mac üzerinde .NET Core uygulamaları geliştirmenin üç yolu için geçerlidir: en sevdiğiniz düzenleyici, [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) [ile komut satırı](tutorials/using-with-xplat-cli.md)aracılığıyla.

## <a name="supported-macos-versions"></a>Desteklenen macOS sürümleri

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

.NET Core 2. x, macOS 'un aşağıdaki sürümlerinde desteklenir:

* macOS 10,12 "Sierra" ve sonraki sürümleri

.NET Core 2,1 ve .NET Core 2,2 tarafından desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümleri ve yaşam döngüsü ilkesi için [.net core 2,1 desteklenen](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) işletim sistemi sürümleri ve [.NET Core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) ' ne bakın Köprü.

İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

.NET Core 1. x, macOS 'un aşağıdaki sürümlerinde desteklenir:

* macOS 10,12 "Sierra"
* macOS 10,11 "El Capitan"

.NET Core 1,1 ve .NET Core 1,0 tarafından desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümleri ve yaşam döngüsü ilkesi için [.net core 1,1 desteklenen](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) işletim sistemi sürümleri ve [.NET Core 1,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) ' ne bakın Köprü.

İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 1,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/1.1) veya [.NET Core 1,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/1.0).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0, macOS 'un aşağıdaki sürümlerinde desteklenir:

* macOS 10,13 "High Sierra" ve sonraki sürümler

.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 3,0 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .

İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0).

---

## <a name="net-core-dependencies"></a>.NET Core bağımlılıkları

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

.NET Core SDK [.net İndirmeleri](https://dotnet.microsoft.com/download) sayfasından indirin ve yükleyin. MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, yüklediğiniz sürüm için [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1) konusuna bakın.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

.NET Core 1. x, macOS üzerinde çalışırken OpenSSL gerektirir. OpenSSL almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır. *Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek OpenSSL 'yi yüklemeniz gerekir:

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

.NET Core SDK [.net İndirmeleri](https://dotnet.microsoft.com/download) sayfasından indirin ve yükleyin. MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) konularına bakın.

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core SDK [.net İndirmeleri](https://dotnet.microsoft.com/download) sayfasından indirin ve yükleyin. MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, yüklediğiniz sürümün [sürüm notları](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) konusuna başvurun.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Açık dosya sınırının üst sınırını artır (.NET Core SDK 2.0.2 önce .NET Core sürümleri)

Eski .NET Core sürümlerinde (.NET Core SDK 2.0.2), macOS 'ta varsayılan açık dosya sınırı, projeleri geri yükleme veya birim testlerini çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.

Bu sınırı aşağıdaki adımları izleyerek artırabilirsiniz:

1. Bir metin düzenleyicisi kullanarak yeni bir _/Library/LaunchDaemons/limit.maxfiles.plist_dosyası oluşturun ve dosyayı bu içerikle kaydedin:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
      <dict>
        <key>Label</key>
        <string>limit.maxfiles</string>
        <key>ProgramArguments</key>
        <array>
          <string>launchctl</string>
          <string>limit</string>
          <string>maxfiles</string>
          <string>2048</string>
          <string>4096</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>ServiceIPC</key>
        <false/>
      </dict>
    </plist>
    ```

2. Bir Terminal penceresinde aşağıdaki komutu çalıştırın:

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. Bu ayarları uygulamak için Mac 'i yeniden başlatın.

## <a name="visual-studio-for-mac"></a>Mac için Visual Studio

.NET Core SDK kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz. Ancak, tümleşik bir geliştirme ortamında Mac 'te .NET Core uygulamaları geliştirmek istiyorsanız [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)kullanabilirsiniz.

MacOS 'ta Mac için Visual Studio .NET Core geliştirmesi şunları gerektirir:

* MacOS işletim sisteminin desteklenen bir sürümü
* OpenSSL (.NET Core 1. x yalnızca .NET Core 2. x, macOS 'ta yerel olarak bulunan güvenlik hizmetlerini kullanır)
* Mac için .NET Core SDK
* [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

---
title: Mac üzerinde .NET Core için Önkoşullar
description: MacOS sürümleri ve geliştirme, dağıtma ve macOS makinelerinde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıklar desteklenmiyor.
author: guardrex
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 12/14/2018
ms.openlocfilehash: 3f5dce25ed03061d690432684975909d15bbad57
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64752958"
---
# <a name="prerequisites-for-net-core-on-macos"></a>MacOS üzerinde .NET Core için Önkoşullar

Bu makalede desteklenen macOS sürümleri ve geliştirme, dağıtma ve macOS makinelerinde .NET Core uygulamaları çalıştırmak için ihtiyacınız olan .NET Core bağımlılıkları gösterir. Desteklenen işletim sistemi sürümleri ve bağımlılıklarını izleyen bir Mac üzerinde .NET Core uygulamaları geliştirme üç yoldan uygulamak: aracılığıyla [komut satırı ile tercih ettiğiniz düzenleyiciyi](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="supported-macos-versions"></a>Desteklenen macOS sürümleri

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET core 2.x, aşağıdaki macOS sürümlerinde desteklenir:

* macOS 10.12 "Sierra" ve sonraki sürümler

Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) ve [.NET Core 2.2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) tam listesi, .NET Core 2.1 ve .NET Core 2.2 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.

Daha fazla bilgi ve indirme bağlantıları [.NET Core 2.2 indirir](https://www.microsoft.com/net/download/dotnet-core/2.2) veya [.NET Core 2.1 yükler](https://www.microsoft.com/net/download/dotnet-core/2.1).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x macOS üzerinde aşağıdaki sürümleri desteklenir:

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Bkz: [.NET Core 1.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) ve [.NET Core 1.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) tam listesi, .NET Core 1.1 ve .NET Core 1.0 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.

Daha fazla bilgi ve indirme bağlantıları [.NET Core 1.1 indirir](https://www.microsoft.com/net/download/dotnet-core/1.1) veya [.NET Core 1.0 indirir](https://www.microsoft.com/net/download/dotnet-core/1.0).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET core 3.0 Preview 3, aşağıdaki macOS sürümlerinde desteklenir:

* macOS 10.12 "Sierra" ve sonraki sürümler

Bkz: [.NET Core 3.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) tam listesi .NET Core 3.0, desteklenen işletim sistemleri, dağıtımlar ve sürümler, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.

Daha fazla bilgi ve indirme bağlantıları [.NET Core 3.0 indirir](https://www.microsoft.com/net/download/dotnet-core/3.0).

---

## <a name="net-core-dependencies"></a>.NET core bağımlılıkları

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core). Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1) yüklü olan sürüm için konu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x macOS üzerinde çalışırken OpenSSL gerektirir. OpenSSL almak için kolay bir yol kullanmaktır [Homebrew ("brew")](https://brew.sh/) macOS için Paket Yöneticisi. Yükledikten sonra *brew*, OpenSSL Terminal (komut) isteminde aşağıdaki komutları çalıştırarak yükleyin:

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core). Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) konuları.

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core). Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [sürüm notları](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) yüklü olan sürüm için konu.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>(.NET Core sürümleri .NET Core SDK'sı 2.0.2 önce) en fazla açık dosya sınırını artırın

(Önce .NET Core SDK 2.0.2) daha eski .NET Core sürümlerinde varsayılan açık dosya sınırı macos'ta projeleri geri yükleme veya birim testleri çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.

Aşağıdaki adımları izleyerek bu sınırı artırabilirsiniz:

1. Bir metin düzenleyicisi kullanarak yeni bir dosya oluşturun _/Library/LaunchDaemons/limit.maxfiles.plist_, söz konusu içeriklerle dosyayı kaydedin:

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

2. Bir terminal penceresinde aşağıdaki komutu çalıştırın:

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. Mac'iniz, bu ayarları uygulamak için yeniden başlatın.

## <a name="visual-studio-for-mac"></a>Mac için Visual Studio

.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz. Ancak, bir tümleşik geliştirme ortamında bir Mac üzerinde .NET Core uygulamaları geliştirmek istiyorsanız, kullanabileceğiniz [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

Mac için Visual Studio ile macOS üzerinde .NET core geliştirme gerektirir:

* MacOS işletim sisteminin desteklenen bir sürümü
* OpenSSL (.NET Core 1.x yalnızca; .NET Core 2.x kullandığı güvenlik hizmetleri yerel olarak macOS kullanılabilir)
* .NET core SDK'sı Mac için
* [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

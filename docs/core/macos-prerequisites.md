---
title: ".NET Core üzerinde Mac için Önkoşullar"
description: "MacOS sürümleri ve geliştirmek, dağıtmak ve macOS makinelerde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıkları desteklenir."
keywords: .NET, .NET core macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.openlocfilehash: 16f3cfd482bddfff1b9ad56e7ffe58ae2aed4980
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
---
# <a name="prerequisites-for-net-core-on-macos"></a>MacOS üzerinde .NET Core için Önkoşullar

Bu makalede, desteklenen macOS sürümleri ve geliştirmek, dağıtmak ve macOS makinelerde .NET Core uygulamaları çalıştırmak için gereken .NET Core bağımlılıkları gösterir. Desteklenen işletim sistemi sürümleri ve izleyin bağımlılıkları Mac'te .NET Core uygulama geliştirme üç yolu için geçerlidir: aracılığıyla [tercih ettiğiniz Düzenleyicisi ile komut satırı](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Desteklenen macOS sürümleri

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET core 2.x macOS aşağıdaki sürümlerinde desteklenir:

* macOS 10,12 "Sierra" ve sonraki sürümler

Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x macOS aşağıdaki sürümlerinde desteklenir:

* macOS 10,12 "Sierra"
* macOS 10.11 sürümünü "El Capitan"

Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.

---

## <a name="net-core-dependencies"></a>.NET core bağımlılıkları

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET Core SDK yükleyip [.NET indirmeleri](https://www.microsoft.com/net/download/core). MacOS üzerinde yükleme sorunları varsa başvurun [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.0) yüklü olan sürüm için konu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**.NET core 1.x**

.NET core 1.x macOS üzerinde çalışırken OpenSSL gerektirir. Kullanarak OpenSSL almak için kolay bir yoludur [Homebrew ("brew")](https://brew.sh/) macOS için Paket Yöneticisi. Yükledikten sonra *brew*, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek OpenSSL yükleyin:

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

.NET Core SDK yükleyip [.NET indirmeleri](https://www.microsoft.com/net/download/core). MacOS üzerinde yükleme sorunları varsa başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) Konular.

---

## <a name="increase-the-maximum-open-file-limit"></a>En fazla açık dosya sınırını artırın

MacOS varsayılan dosya Aç sınırı projeleri geri yükleme veya birim testleri çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.

Aşağıdaki adımları izleyerek bu sınırı artırabilirsiniz:

1. Bir metin düzenleyicisi kullanarak yeni bir dosya oluşturmak _/Library/LaunchDaemons/limit.maxfiles.plist_ve bu içeriği dosyayı kaydedin:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
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

3. Bu ayarları uygulamak için Mac bilgisayarınızı yeniden başlatın.

## <a name="visual-studio-for-mac"></a>Mac için Visual Studio

.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir Düzenleyicisi'ni kullanabilirsiniz. Ancak, bir tümleşik geliştirme ortamında Mac'te .NET Core uygulamaları geliştirmek istiyorsanız kullanabileceğiniz [Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/). 

Mac için Visual Studio ile macOS üzerinde .NET core geliştirme gerektirir:

* MacOS işletim sisteminin desteklenen bir sürümü
* OpenSSL (.NET Core yalnızca 1.x; .NET Core 2.x kullandığı güvenlik hizmetleri yerel olarak macOS kullanılabilir)
* .NET core Mac için SDK'sı
* [Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/)

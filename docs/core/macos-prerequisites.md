---
title: .NET Core üzerinde Mac için Önkoşullar
description: MacOS sürümleri ve geliştirmek, dağıtmak ve macOS makinelerde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıkları desteklenir.
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 2644cd491d1d3ba07f48f57fd9416ec84316f7d8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="86d74-103">MacOS üzerinde .NET Core için Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="86d74-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="86d74-104">Bu makalede, desteklenen macOS sürümleri ve geliştirmek, dağıtmak ve macOS makinelerde .NET Core uygulamaları çalıştırmak için gereken .NET Core bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="86d74-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="86d74-105">Desteklenen işletim sistemi sürümleri ve izleyin bağımlılıkları Mac'te .NET Core uygulama geliştirme üç yolu için geçerlidir: aracılığıyla [tercih ettiğiniz Düzenleyicisi ile komut satırı](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="86d74-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="86d74-106">Desteklenen macOS sürümleri</span><span class="sxs-lookup"><span data-stu-id="86d74-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="86d74-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="86d74-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="86d74-108">.NET core 2.x macOS aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="86d74-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="86d74-109">macOS 10,12 "Sierra" ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="86d74-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="86d74-110">Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="86d74-110">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="86d74-111">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="86d74-111">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="86d74-112">.NET core 1.x macOS aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="86d74-112">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="86d74-113">macOS 10,12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="86d74-113">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="86d74-114">macOS 10.11 sürümünü "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="86d74-114">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="86d74-115">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="86d74-115">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="86d74-116">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="86d74-116">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="86d74-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="86d74-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="86d74-118">.NET Core SDK yükleyip [.NET indirmeleri](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="86d74-118">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="86d74-119">MacOS üzerinde yükleme sorunları varsa başvurun [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.0) yüklü olan sürüm için konu.</span><span class="sxs-lookup"><span data-stu-id="86d74-119">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="86d74-120">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="86d74-120">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="86d74-121">**.NET core 1.x**</span><span class="sxs-lookup"><span data-stu-id="86d74-121">**.NET Core 1.x**</span></span>

<span data-ttu-id="86d74-122">.NET core 1.x macOS üzerinde çalışırken OpenSSL gerektirir.</span><span class="sxs-lookup"><span data-stu-id="86d74-122">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="86d74-123">Kullanarak OpenSSL almak için kolay bir yoludur [Homebrew ("brew")](https://brew.sh/) macOS için Paket Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="86d74-123">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="86d74-124">Yükledikten sonra *brew*, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek OpenSSL yükleyin:</span><span class="sxs-lookup"><span data-stu-id="86d74-124">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="86d74-125">.NET Core SDK yükleyip [.NET indirmeleri](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="86d74-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="86d74-126">MacOS üzerinde yükleme sorunları varsa başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) Konular.</span><span class="sxs-lookup"><span data-stu-id="86d74-126">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="86d74-127">En fazla açık dosya sınırını (.NET Core SDK 2.0.2 önce .NET Core sürümler)</span><span class="sxs-lookup"><span data-stu-id="86d74-127">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="86d74-128">(Önce .NET Core SDK 2.0.2) eski .NET Core sürümlerde macOS varsayılan dosya Aç sınırı projeleri geri yükleme veya birim testleri çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="86d74-128">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="86d74-129">Aşağıdaki adımları izleyerek bu sınırı artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86d74-129">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="86d74-130">Bir metin düzenleyicisi kullanarak yeni bir dosya oluşturmak _/Library/LaunchDaemons/limit.maxfiles.plist_ve bu içeriği dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="86d74-130">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="86d74-131">Bir terminal penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="86d74-131">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="86d74-132">Bu ayarları uygulamak için Mac bilgisayarınızı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="86d74-132">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="86d74-133">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86d74-133">Visual Studio for Mac</span></span>

<span data-ttu-id="86d74-134">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir Düzenleyicisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d74-134">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="86d74-135">Ancak, bir tümleşik geliştirme ortamında Mac'te .NET Core uygulamaları geliştirmek istiyorsanız kullanabileceğiniz [Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="86d74-135">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="86d74-136">Mac için Visual Studio ile macOS üzerinde .NET core geliştirme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="86d74-136">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="86d74-137">MacOS işletim sisteminin desteklenen bir sürümü</span><span class="sxs-lookup"><span data-stu-id="86d74-137">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="86d74-138">OpenSSL (.NET Core yalnızca 1.x; .NET Core 2.x kullandığı güvenlik hizmetleri yerel olarak macOS kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="86d74-138">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="86d74-139">.NET core Mac için SDK'sı</span><span class="sxs-lookup"><span data-stu-id="86d74-139">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="86d74-140">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86d74-140">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

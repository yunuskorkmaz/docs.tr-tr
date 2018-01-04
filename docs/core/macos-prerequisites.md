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
ms.workload: dotnetcore
ms.openlocfilehash: 5aac7566f532312c890bad07c901929ae826ece3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="bcd03-104">MacOS üzerinde .NET Core için Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="bcd03-104">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="bcd03-105">Bu makalede, desteklenen macOS sürümleri ve geliştirmek, dağıtmak ve macOS makinelerde .NET Core uygulamaları çalıştırmak için gereken .NET Core bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcd03-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="bcd03-106">Desteklenen işletim sistemi sürümleri ve izleyin bağımlılıkları Mac'te .NET Core uygulama geliştirme üç yolu için geçerlidir: aracılığıyla [tercih ettiğiniz Düzenleyicisi ile komut satırı](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="bcd03-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="bcd03-107">Desteklenen macOS sürümleri</span><span class="sxs-lookup"><span data-stu-id="bcd03-107">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bcd03-108">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bcd03-108">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bcd03-109">.NET core 2.x macOS aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="bcd03-109">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="bcd03-110">macOS 10,12 "Sierra" ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="bcd03-110">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="bcd03-111">Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="bcd03-111">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bcd03-112">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bcd03-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bcd03-113">.NET core 1.x macOS aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="bcd03-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="bcd03-114">macOS 10,12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="bcd03-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="bcd03-115">macOS 10.11 sürümünü "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="bcd03-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="bcd03-116">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="bcd03-116">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="bcd03-117">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="bcd03-117">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bcd03-118">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bcd03-118">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bcd03-119">.NET Core SDK yükleyip [.NET indirmeleri](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="bcd03-119">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="bcd03-120">MacOS üzerinde yükleme sorunları varsa başvurun [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.0) yüklü olan sürüm için konu.</span><span class="sxs-lookup"><span data-stu-id="bcd03-120">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bcd03-121">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bcd03-121">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bcd03-122">**.NET core 1.x**</span><span class="sxs-lookup"><span data-stu-id="bcd03-122">**.NET Core 1.x**</span></span>

<span data-ttu-id="bcd03-123">.NET core 1.x macOS üzerinde çalışırken OpenSSL gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bcd03-123">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="bcd03-124">Kullanarak OpenSSL almak için kolay bir yoludur [Homebrew ("brew")](https://brew.sh/) macOS için Paket Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="bcd03-124">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="bcd03-125">Yükledikten sonra *brew*, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek OpenSSL yükleyin:</span><span class="sxs-lookup"><span data-stu-id="bcd03-125">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="bcd03-126">.NET Core SDK yükleyip [.NET indirmeleri](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="bcd03-126">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="bcd03-127">MacOS üzerinde yükleme sorunları varsa başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) Konular.</span><span class="sxs-lookup"><span data-stu-id="bcd03-127">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit"></a><span data-ttu-id="bcd03-128">En fazla açık dosya sınırını artırın</span><span class="sxs-lookup"><span data-stu-id="bcd03-128">Increase the maximum open file limit</span></span>

<span data-ttu-id="bcd03-129">MacOS varsayılan dosya Aç sınırı projeleri geri yükleme veya birim testleri çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="bcd03-129">The default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="bcd03-130">Aşağıdaki adımları izleyerek bu sınırı artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bcd03-130">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="bcd03-131">Bir metin düzenleyicisi kullanarak yeni bir dosya oluşturmak _/Library/LaunchDaemons/limit.maxfiles.plist_ve bu içeriği dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="bcd03-131">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="bcd03-132">Bir terminal penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="bcd03-132">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="bcd03-133">Bu ayarları uygulamak için Mac bilgisayarınızı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="bcd03-133">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="bcd03-134">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bcd03-134">Visual Studio for Mac</span></span>

<span data-ttu-id="bcd03-135">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir Düzenleyicisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcd03-135">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="bcd03-136">Ancak, bir tümleşik geliştirme ortamında Mac'te .NET Core uygulamaları geliştirmek istiyorsanız kullanabileceğiniz [Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="bcd03-136">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="bcd03-137">Mac için Visual Studio ile macOS üzerinde .NET core geliştirme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bcd03-137">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="bcd03-138">MacOS işletim sisteminin desteklenen bir sürümü</span><span class="sxs-lookup"><span data-stu-id="bcd03-138">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="bcd03-139">OpenSSL (.NET Core yalnızca 1.x; .NET Core 2.x kullandığı güvenlik hizmetleri yerel olarak macOS kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="bcd03-139">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="bcd03-140">.NET core Mac için SDK'sı</span><span class="sxs-lookup"><span data-stu-id="bcd03-140">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="bcd03-141">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bcd03-141">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

---
title: Mac üzerinde .NET Core için Önkoşullar
description: MacOS sürümleri ve geliştirme, dağıtma ve macOS makinelerinde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıklar desteklenmiyor.
author: guardrex
ms.author: mairaw
ms.date: 10/03/2018
ms.openlocfilehash: b5b3c6ea90a2cc4487e849af468d324b645834af
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584084"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="2b5e3-103">MacOS üzerinde .NET Core için Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2b5e3-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="2b5e3-104">Bu makalede desteklenen macOS sürümleri ve geliştirme, dağıtma ve macOS makinelerinde .NET Core uygulamaları çalıştırmak için ihtiyacınız olan .NET Core bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="2b5e3-105">Desteklenen işletim sistemi sürümleri ve bağımlılıklarını izleyen bir Mac üzerinde .NET Core uygulamaları geliştirme üç yoldan uygulamak: aracılığıyla [komut satırı ile tercih ettiğiniz düzenleyiciyi](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="2b5e3-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="2b5e3-106">Desteklenen macOS sürümleri</span><span class="sxs-lookup"><span data-stu-id="2b5e3-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2b5e3-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="2b5e3-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="2b5e3-108">.NET core 2.x, aşağıdaki macOS sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="2b5e3-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="2b5e3-109">macOS 10.12 "Sierra" ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="2b5e3-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="2b5e3-110">Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-110">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2b5e3-111">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="2b5e3-111">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="2b5e3-112">.NET core 1.x macOS üzerinde aşağıdaki sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="2b5e3-112">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="2b5e3-113">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="2b5e3-113">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="2b5e3-114">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="2b5e3-114">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="2b5e3-115">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-115">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="2b5e3-116">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="2b5e3-116">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2b5e3-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="2b5e3-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="2b5e3-118">.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="2b5e3-118">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="2b5e3-119">Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1) yüklü olan sürüm için konu.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-119">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2b5e3-120">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="2b5e3-120">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="2b5e3-121">**.NET core 1.x**</span><span class="sxs-lookup"><span data-stu-id="2b5e3-121">**.NET Core 1.x**</span></span>

<span data-ttu-id="2b5e3-122">.NET core 1.x macOS üzerinde çalışırken OpenSSL gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-122">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="2b5e3-123">OpenSSL almak için kolay bir yol kullanmaktır [Homebrew ("brew")](https://brew.sh/) macOS için Paket Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-123">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="2b5e3-124">Yükledikten sonra *brew*, OpenSSL Terminal (komut) isteminde aşağıdaki komutları çalıştırarak yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2b5e3-124">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="2b5e3-125">.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="2b5e3-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="2b5e3-126">Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-126">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="2b5e3-127">(.NET Core sürümleri .NET Core SDK'sı 2.0.2 önce) en fazla açık dosya sınırını artırın</span><span class="sxs-lookup"><span data-stu-id="2b5e3-127">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="2b5e3-128">(Önce .NET Core SDK 2.0.2) daha eski .NET Core sürümlerinde varsayılan açık dosya sınırı macos'ta projeleri geri yükleme veya birim testleri çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-128">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="2b5e3-129">Aşağıdaki adımları izleyerek bu sınırı artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b5e3-129">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="2b5e3-130">Bir metin düzenleyicisi kullanarak yeni bir dosya oluşturun _/Library/LaunchDaemons/limit.maxfiles.plist_, söz konusu içeriklerle dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="2b5e3-130">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="2b5e3-131">Bir terminal penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2b5e3-131">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="2b5e3-132">Mac'iniz, bu ayarları uygulamak için yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-132">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="2b5e3-133">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2b5e3-133">Visual Studio for Mac</span></span>

<span data-ttu-id="2b5e3-134">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5e3-134">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="2b5e3-135">Ancak, bir tümleşik geliştirme ortamında bir Mac üzerinde .NET Core uygulamaları geliştirmek istiyorsanız, kullanabileceğiniz [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="2b5e3-135">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="2b5e3-136">Mac için Visual Studio ile macOS üzerinde .NET core geliştirme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2b5e3-136">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="2b5e3-137">MacOS işletim sisteminin desteklenen bir sürümü</span><span class="sxs-lookup"><span data-stu-id="2b5e3-137">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="2b5e3-138">OpenSSL (.NET Core 1.x yalnızca; .NET Core 2.x kullandığı güvenlik hizmetleri yerel olarak macOS kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="2b5e3-138">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="2b5e3-139">.NET core SDK'sı Mac için</span><span class="sxs-lookup"><span data-stu-id="2b5e3-139">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="2b5e3-140">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2b5e3-140">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/visual-studio-mac/)

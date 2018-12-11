---
title: Mac üzerinde .NET Core için Önkoşullar
description: MacOS sürümleri ve geliştirme, dağıtma ve macOS makinelerinde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıklar desteklenmiyor.
author: guardrex
ms.author: adegeo
ms.date: 12/03/2018
ms.openlocfilehash: b2ab86b7eb9faeab8d4a4cac92b361f64517f638
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145638"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="3b584-103">MacOS üzerinde .NET Core için Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3b584-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="3b584-104">Bu makalede desteklenen macOS sürümleri ve geliştirme, dağıtma ve macOS makinelerinde .NET Core uygulamaları çalıştırmak için ihtiyacınız olan .NET Core bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b584-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="3b584-105">Desteklenen işletim sistemi sürümleri ve bağımlılıklarını izleyen bir Mac üzerinde .NET Core uygulamaları geliştirme üç yoldan uygulamak: aracılığıyla [komut satırı ile tercih ettiğiniz düzenleyiciyi](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="3b584-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="3b584-106">Desteklenen macOS sürümleri</span><span class="sxs-lookup"><span data-stu-id="3b584-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3b584-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="3b584-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="3b584-108">.NET core 2.x, aşağıdaki macOS sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3b584-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="3b584-109">macOS 10.12 "Sierra" ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="3b584-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="3b584-110">Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) ve [.NET Core 2.2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) tam listesi, .NET Core 2.1 ve .NET Core 2.2 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="3b584-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="3b584-111">Daha fazla bilgi ve indirme bağlantıları [.NET Core 2.2 indirir](https://www.microsoft.com/net/download/dotnet-core/2.2) veya [.NET Core 2.1 yükler](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="3b584-111">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>


# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b584-112">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b584-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3b584-113">.NET core 1.x macOS üzerinde aşağıdaki sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3b584-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="3b584-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="3b584-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="3b584-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="3b584-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="3b584-116">Bkz: [.NET Core 1.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) ve [.NET Core 1.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) tam listesi, .NET Core 1.1 ve .NET Core 1.0 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="3b584-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="3b584-117">Daha fazla bilgi ve indirme bağlantıları [.NET Core 1.1 indirir](https://www.microsoft.com/net/download/dotnet-core/1.1) veya [.NET Core 1.0 indirir](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="3b584-117">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="3b584-118">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="3b584-118">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3b584-119">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="3b584-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="3b584-120">.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="3b584-120">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="3b584-121">Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1) yüklü olan sürüm için konu.</span><span class="sxs-lookup"><span data-stu-id="3b584-121">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b584-122">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b584-122">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3b584-123">**.NET core 1.x**</span><span class="sxs-lookup"><span data-stu-id="3b584-123">**.NET Core 1.x**</span></span>

<span data-ttu-id="3b584-124">.NET core 1.x macOS üzerinde çalışırken OpenSSL gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3b584-124">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="3b584-125">OpenSSL almak için kolay bir yol kullanmaktır [Homebrew ("brew")](https://brew.sh/) macOS için Paket Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="3b584-125">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="3b584-126">Yükledikten sonra *brew*, OpenSSL Terminal (komut) isteminde aşağıdaki komutları çalıştırarak yükleyin:</span><span class="sxs-lookup"><span data-stu-id="3b584-126">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="3b584-127">.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="3b584-127">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="3b584-128">Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="3b584-128">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="3b584-129">(.NET Core sürümleri .NET Core SDK'sı 2.0.2 önce) en fazla açık dosya sınırını artırın</span><span class="sxs-lookup"><span data-stu-id="3b584-129">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="3b584-130">(Önce .NET Core SDK 2.0.2) daha eski .NET Core sürümlerinde varsayılan açık dosya sınırı macos'ta projeleri geri yükleme veya birim testleri çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3b584-130">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="3b584-131">Aşağıdaki adımları izleyerek bu sınırı artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b584-131">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="3b584-132">Bir metin düzenleyicisi kullanarak yeni bir dosya oluşturun _/Library/LaunchDaemons/limit.maxfiles.plist_, söz konusu içeriklerle dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="3b584-132">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="3b584-133">Bir terminal penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3b584-133">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="3b584-134">Mac'iniz, bu ayarları uygulamak için yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="3b584-134">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="3b584-135">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b584-135">Visual Studio for Mac</span></span>

<span data-ttu-id="3b584-136">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b584-136">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="3b584-137">Ancak, bir tümleşik geliştirme ortamında bir Mac üzerinde .NET Core uygulamaları geliştirmek istiyorsanız, kullanabileceğiniz [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="3b584-137">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="3b584-138">Mac için Visual Studio ile macOS üzerinde .NET core geliştirme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3b584-138">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="3b584-139">MacOS işletim sisteminin desteklenen bir sürümü</span><span class="sxs-lookup"><span data-stu-id="3b584-139">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="3b584-140">OpenSSL (.NET Core 1.x yalnızca; .NET Core 2.x kullandığı güvenlik hizmetleri yerel olarak macOS kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="3b584-140">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="3b584-141">.NET core SDK'sı Mac için</span><span class="sxs-lookup"><span data-stu-id="3b584-141">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="3b584-142">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b584-142">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/visual-studio-mac/)

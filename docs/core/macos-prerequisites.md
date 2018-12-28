---
title: Mac üzerinde .NET Core için Önkoşullar
description: MacOS sürümleri ve geliştirme, dağıtma ve macOS makinelerinde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıklar desteklenmiyor.
author: guardrex
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: bc6e0b20c61c474c7069b757528dbc1ea38354e3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656316"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="823d8-103">MacOS üzerinde .NET Core için Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="823d8-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="823d8-104">Bu makalede desteklenen macOS sürümleri ve geliştirme, dağıtma ve macOS makinelerinde .NET Core uygulamaları çalıştırmak için ihtiyacınız olan .NET Core bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="823d8-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="823d8-105">Desteklenen işletim sistemi sürümleri ve bağımlılıklarını izleyen bir Mac üzerinde .NET Core uygulamaları geliştirme üç yoldan uygulamak: aracılığıyla [komut satırı ile tercih ettiğiniz düzenleyiciyi](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="823d8-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="823d8-106">Desteklenen macOS sürümleri</span><span class="sxs-lookup"><span data-stu-id="823d8-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="823d8-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="823d8-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="823d8-108">.NET core 2.x, aşağıdaki macOS sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="823d8-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="823d8-109">macOS 10.12 "Sierra" ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="823d8-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="823d8-110">Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) ve [.NET Core 2.2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) tam listesi, .NET Core 2.1 ve .NET Core 2.2 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="823d8-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="823d8-111">Daha fazla bilgi ve indirme bağlantıları [.NET Core 2.2 indirir](https://www.microsoft.com/net/download/dotnet-core/2.2) veya [.NET Core 2.1 yükler](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="823d8-111">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>


# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="823d8-112">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="823d8-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="823d8-113">.NET core 1.x macOS üzerinde aşağıdaki sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="823d8-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="823d8-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="823d8-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="823d8-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="823d8-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="823d8-116">Bkz: [.NET Core 1.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) ve [.NET Core 1.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) tam listesi, .NET Core 1.1 ve .NET Core 1.0 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="823d8-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="823d8-117">Daha fazla bilgi ve indirme bağlantıları [.NET Core 1.1 indirir](https://www.microsoft.com/net/download/dotnet-core/1.1) veya [.NET Core 1.0 indirir](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="823d8-117">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="823d8-118">.NET core 3.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="823d8-118">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="823d8-119">.NET core 3.0 Önizleme 1 macOS üzerinde aşağıdaki sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="823d8-119">.NET Core 3.0 Preview 1 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="823d8-120">macOS 10.12 "Sierra" ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="823d8-120">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="823d8-121">Bkz: [.NET Core 3.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) tam listesi .NET Core 3.0, desteklenen işletim sistemleri, dağıtımlar ve sürümler, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="823d8-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="823d8-122">Daha fazla bilgi ve indirme bağlantıları [.NET Core 3.0 indirir](https://www.microsoft.com/net/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="823d8-122">For download links and more information, see [.NET Core 3.0 downloads](https://www.microsoft.com/net/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="823d8-123">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="823d8-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="823d8-124">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="823d8-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="823d8-125">.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="823d8-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="823d8-126">Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1) yüklü olan sürüm için konu.</span><span class="sxs-lookup"><span data-stu-id="823d8-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="823d8-127">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="823d8-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="823d8-128">.NET core 1.x macOS üzerinde çalışırken OpenSSL gerektirir.</span><span class="sxs-lookup"><span data-stu-id="823d8-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="823d8-129">OpenSSL almak için kolay bir yol kullanmaktır [Homebrew ("brew")](https://brew.sh/) macOS için Paket Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="823d8-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="823d8-130">Yükledikten sonra *brew*, OpenSSL Terminal (komut) isteminde aşağıdaki komutları çalıştırarak yükleyin:</span><span class="sxs-lookup"><span data-stu-id="823d8-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="823d8-131">.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="823d8-131">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="823d8-132">Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="823d8-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="823d8-133">.NET core 3.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="823d8-133">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="823d8-134">.NET Core SDK'sından yükleyip [.NET indirir](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="823d8-134">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="823d8-135">Macos'ta yükleme ile ilgili sorunlar varsa, başvurun [sürüm notları](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) yüklü olan sürüm için konu.</span><span class="sxs-lookup"><span data-stu-id="823d8-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="823d8-136">(.NET Core sürümleri .NET Core SDK'sı 2.0.2 önce) en fazla açık dosya sınırını artırın</span><span class="sxs-lookup"><span data-stu-id="823d8-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="823d8-137">(Önce .NET Core SDK 2.0.2) daha eski .NET Core sürümlerinde varsayılan açık dosya sınırı macos'ta projeleri geri yükleme veya birim testleri çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="823d8-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="823d8-138">Aşağıdaki adımları izleyerek bu sınırı artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="823d8-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="823d8-139">Bir metin düzenleyicisi kullanarak yeni bir dosya oluşturun _/Library/LaunchDaemons/limit.maxfiles.plist_, söz konusu içeriklerle dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="823d8-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="823d8-140">Bir terminal penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="823d8-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="823d8-141">Mac'iniz, bu ayarları uygulamak için yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="823d8-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="823d8-142">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="823d8-142">Visual Studio for Mac</span></span>

<span data-ttu-id="823d8-143">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="823d8-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="823d8-144">Ancak, bir tümleşik geliştirme ortamında bir Mac üzerinde .NET Core uygulamaları geliştirmek istiyorsanız, kullanabileceğiniz [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="823d8-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="823d8-145">Mac için Visual Studio ile macOS üzerinde .NET core geliştirme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="823d8-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="823d8-146">MacOS işletim sisteminin desteklenen bir sürümü</span><span class="sxs-lookup"><span data-stu-id="823d8-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="823d8-147">OpenSSL (.NET Core 1.x yalnızca; .NET Core 2.x kullandığı güvenlik hizmetleri yerel olarak macOS kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="823d8-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="823d8-148">.NET core SDK'sı Mac için</span><span class="sxs-lookup"><span data-stu-id="823d8-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="823d8-149">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="823d8-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/visual-studio-mac/)

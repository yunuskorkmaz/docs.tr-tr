---
title: Mac üzerinde .NET Core önkoşulları
description: MacOS makinelerinde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen macOS sürümleri ve .NET Core bağımlılıkları.
author: mairaw
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 07/13/2019
ms.openlocfilehash: 5086b185ee2d49c7b569ed0cb62b4c8995f9982c
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433908"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="0387d-103">MacOS 'ta .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="0387d-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="0387d-104">Bu makalede, macOS makinelerinde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için ihtiyacınız olan desteklenen macOS sürümleri ve .NET Core bağımlılıkları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0387d-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="0387d-105">Desteklenen işletim sistemi sürümleri ve bağımlılıklar, bir Mac üzerinde .NET Core uygulamaları geliştirmenin üç yolu için geçerlidir: en sevdiğiniz düzenleyici, [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) [ile komut satırı](tutorials/using-with-xplat-cli.md)aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="0387d-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="0387d-106">Desteklenen macOS sürümleri</span><span class="sxs-lookup"><span data-stu-id="0387d-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0387d-107">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="0387d-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="0387d-108">.NET Core 2. x, macOS 'un aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0387d-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="0387d-109">macOS 10,12 "Sierra" ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="0387d-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="0387d-110">.NET Core 2,1 ve .NET Core 2,2 tarafından desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümleri ve yaşam döngüsü ilkesi için [.net core 2,1 desteklenen](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) işletim sistemi sürümleri ve [.NET Core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) ' ne bakın Köprü.</span><span class="sxs-lookup"><span data-stu-id="0387d-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="0387d-111">İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 2,2 İndirmeleri](https://www.microsoft.com/net/download/dotnet-core/2.2) veya [.NET Core 2,1 İndirmeleri](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="0387d-111">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0387d-112">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="0387d-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0387d-113">.NET Core 1. x, macOS 'un aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0387d-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="0387d-114">macOS 10,12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="0387d-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="0387d-115">macOS 10,11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="0387d-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="0387d-116">.NET Core 1,1 ve .NET Core 1,0 tarafından desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümleri ve yaşam döngüsü ilkesi için [.net core 1,1 desteklenen](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) işletim sistemi sürümleri ve [.NET Core 1,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) ' ne bakın Köprü.</span><span class="sxs-lookup"><span data-stu-id="0387d-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="0387d-117">İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 1,1 İndirmeleri](https://www.microsoft.com/net/download/dotnet-core/1.1) veya [.NET Core 1,0 İndirmeleri](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="0387d-117">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="0387d-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0387d-118">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="0387d-119">.NET Core 3,0, macOS 'un aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0387d-119">.NET Core 3.0 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="0387d-120">macOS 10,13 "High Sierra" ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="0387d-120">macOS 10.13 "High Sierra" and later versions</span></span>

<span data-ttu-id="0387d-121">.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 3,0 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="0387d-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="0387d-122">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 3,0 İndirmeleri](https://www.microsoft.com/net/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="0387d-122">For download links and more information, see [.NET Core 3.0 downloads](https://www.microsoft.com/net/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="0387d-123">.NET Core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="0387d-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0387d-124">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="0387d-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="0387d-125">.NET Core SDK [.net Indirmelerinde](https://www.microsoft.com/net/download/core)indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0387d-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="0387d-126">MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, yüklediğiniz sürüm için [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="0387d-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0387d-127">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="0387d-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0387d-128">.NET Core 1. x, macOS üzerinde çalışırken OpenSSL gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0387d-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="0387d-129">OpenSSL almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0387d-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="0387d-130">*Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek OpenSSL 'yi yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="0387d-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="0387d-131">.NET Core SDK [.net Indirmelerinde](https://www.microsoft.com/net/download/core)indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0387d-131">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="0387d-132">MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) konularına bakın.</span><span class="sxs-lookup"><span data-stu-id="0387d-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="0387d-133">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0387d-133">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="0387d-134">.NET Core SDK [.net Indirmelerinde](https://www.microsoft.com/net/download/core)indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0387d-134">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="0387d-135">MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, yüklediğiniz sürümün [sürüm notları](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="0387d-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="0387d-136">Açık dosya sınırının üst sınırını artır (.NET Core SDK 2.0.2 önce .NET Core sürümleri)</span><span class="sxs-lookup"><span data-stu-id="0387d-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span>

<span data-ttu-id="0387d-137">Eski .NET Core sürümlerinde (.NET Core SDK 2.0.2), macOS 'ta varsayılan açık dosya sınırı, projeleri geri yükleme veya birim testlerini çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0387d-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="0387d-138">Bu sınırı aşağıdaki adımları izleyerek artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0387d-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="0387d-139">Bir metin düzenleyicisi kullanarak yeni bir _/Library/LaunchDaemons/limit.maxfiles.plist_dosyası oluşturun ve dosyayı bu içerikle kaydedin:</span><span class="sxs-lookup"><span data-stu-id="0387d-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="0387d-140">Bir Terminal penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0387d-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="0387d-141">Bu ayarları uygulamak için Mac 'i yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="0387d-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="0387d-142">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0387d-142">Visual Studio for Mac</span></span>

<span data-ttu-id="0387d-143">.NET Core SDK kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0387d-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="0387d-144">Ancak, tümleşik bir geliştirme ortamında Mac 'te .NET Core uygulamaları geliştirmek istiyorsanız [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0387d-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

<span data-ttu-id="0387d-145">MacOS 'ta Mac için Visual Studio .NET Core geliştirmesi şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0387d-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="0387d-146">MacOS işletim sisteminin desteklenen bir sürümü</span><span class="sxs-lookup"><span data-stu-id="0387d-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="0387d-147">OpenSSL (.NET Core 1. x yalnızca .NET Core 2. x, macOS 'ta yerel olarak bulunan güvenlik hizmetlerini kullanır)</span><span class="sxs-lookup"><span data-stu-id="0387d-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="0387d-148">Mac için .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="0387d-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="0387d-149">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0387d-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

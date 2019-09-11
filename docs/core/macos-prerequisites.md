---
title: Mac üzerinde .NET Core önkoşulları
description: MacOS makinelerinde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen macOS sürümleri ve .NET Core bağımlılıkları.
author: mairaw
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 07/13/2019
ms.openlocfilehash: 4e0570beb0dd096d7d11cdcfb6a7ed20221c0386
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848960"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="705a7-103">MacOS 'ta .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="705a7-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="705a7-104">Bu makalede, macOS makinelerinde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için ihtiyacınız olan desteklenen macOS sürümleri ve .NET Core bağımlılıkları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="705a7-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="705a7-105">Desteklenen işletim sistemi sürümleri ve bağımlılıklar, bir Mac üzerinde .NET Core uygulamaları geliştirmenin üç yolu için geçerlidir: en sevdiğiniz düzenleyici, [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) [ile komut satırı](tutorials/using-with-xplat-cli.md)aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="705a7-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="705a7-106">Desteklenen macOS sürümleri</span><span class="sxs-lookup"><span data-stu-id="705a7-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="705a7-107">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="705a7-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="705a7-108">.NET Core 2. x, macOS 'un aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="705a7-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="705a7-109">macOS 10,12 "Sierra" ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="705a7-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="705a7-110">.NET Core 2,1 ve .NET Core 2,2 tarafından desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümleri ve yaşam döngüsü ilkesi için [.net core 2,1 desteklenen](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) işletim sistemi sürümleri ve [.NET Core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) ' ne bakın Köprü.</span><span class="sxs-lookup"><span data-stu-id="705a7-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="705a7-111">İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="705a7-111">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="705a7-112">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="705a7-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="705a7-113">.NET Core 1. x, macOS 'un aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="705a7-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="705a7-114">macOS 10,12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="705a7-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="705a7-115">macOS 10,11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="705a7-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="705a7-116">.NET Core 1,1 ve .NET Core 1,0 tarafından desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümleri ve yaşam döngüsü ilkesi için [.net core 1,1 desteklenen](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) işletim sistemi sürümleri ve [.NET Core 1,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) ' ne bakın Köprü.</span><span class="sxs-lookup"><span data-stu-id="705a7-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="705a7-117">İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 1,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/1.1) veya [.NET Core 1,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="705a7-117">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="705a7-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="705a7-118">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="705a7-119">.NET Core 3,0, macOS 'un aşağıdaki sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="705a7-119">.NET Core 3.0 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="705a7-120">macOS 10,13 "High Sierra" ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="705a7-120">macOS 10.13 "High Sierra" and later versions</span></span>

<span data-ttu-id="705a7-121">.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 3,0 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="705a7-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="705a7-122">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="705a7-122">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="705a7-123">.NET Core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="705a7-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="705a7-124">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="705a7-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="705a7-125">.NET Core SDK [.net İndirmeleri](https://dotnet.microsoft.com/download) sayfasından indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="705a7-125">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="705a7-126">MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, yüklediğiniz sürüm için [bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="705a7-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="705a7-127">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="705a7-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="705a7-128">.NET Core 1. x, macOS üzerinde çalışırken OpenSSL gerektirir.</span><span class="sxs-lookup"><span data-stu-id="705a7-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="705a7-129">OpenSSL almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="705a7-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="705a7-130">*Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek OpenSSL 'yi yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="705a7-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="705a7-131">.NET Core SDK [.net İndirmeleri](https://dotnet.microsoft.com/download) sayfasından indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="705a7-131">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="705a7-132">MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) konularına bakın.</span><span class="sxs-lookup"><span data-stu-id="705a7-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="705a7-133">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="705a7-133">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="705a7-134">.NET Core SDK [.net İndirmeleri](https://dotnet.microsoft.com/download) sayfasından indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="705a7-134">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="705a7-135">MacOS üzerinde yüklemeyle ilgili sorunlar yaşıyorsanız, yüklediğiniz sürümün [sürüm notları](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="705a7-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="705a7-136">Açık dosya sınırının üst sınırını artır (.NET Core SDK 2.0.2 önce .NET Core sürümleri)</span><span class="sxs-lookup"><span data-stu-id="705a7-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span>

<span data-ttu-id="705a7-137">Eski .NET Core sürümlerinde (.NET Core SDK 2.0.2), macOS 'ta varsayılan açık dosya sınırı, projeleri geri yükleme veya birim testlerini çalıştırma gibi bazı .NET Core iş yükleri için yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="705a7-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="705a7-138">Bu sınırı aşağıdaki adımları izleyerek artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="705a7-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="705a7-139">Bir metin düzenleyicisi kullanarak yeni bir _/Library/LaunchDaemons/limit.maxfiles.plist_dosyası oluşturun ve dosyayı bu içerikle kaydedin:</span><span class="sxs-lookup"><span data-stu-id="705a7-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="705a7-140">Bir Terminal penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="705a7-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="705a7-141">Bu ayarları uygulamak için Mac 'i yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="705a7-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="705a7-142">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="705a7-142">Visual Studio for Mac</span></span>

<span data-ttu-id="705a7-143">.NET Core SDK kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705a7-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="705a7-144">Ancak, tümleşik bir geliştirme ortamında Mac 'te .NET Core uygulamaları geliştirmek istiyorsanız [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705a7-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

<span data-ttu-id="705a7-145">MacOS 'ta Mac için Visual Studio .NET Core geliştirmesi şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="705a7-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="705a7-146">MacOS işletim sisteminin desteklenen bir sürümü</span><span class="sxs-lookup"><span data-stu-id="705a7-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="705a7-147">OpenSSL (.NET Core 1. x yalnızca .NET Core 2. x, macOS 'ta yerel olarak bulunan güvenlik hizmetlerini kullanır)</span><span class="sxs-lookup"><span data-stu-id="705a7-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="705a7-148">Mac için .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="705a7-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="705a7-149">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="705a7-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

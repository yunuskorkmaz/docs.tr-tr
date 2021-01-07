---
title: Linux 'ta .NET 'i Snap-.NET ile yükler
description: Linux 'ta .NET SDK veya .NET çalışma zamanının yaslama ile nasıl yükleneceğini gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 741933b5ca6f01d73b388675fe7f8a43c4efb0f9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970974"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a><span data-ttu-id="9af11-103">.NET SDK veya .NET çalışma zamanını yaslama ile birlikte yükler</span><span class="sxs-lookup"><span data-stu-id="9af11-103">Install the .NET SDK or the .NET Runtime with Snap</span></span>

<span data-ttu-id="9af11-104">.NET SDK veya .NET çalışma zamanı yüklemek için bir snap paketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9af11-104">Use a Snap package to install the .NET SDK or .NET Runtime.</span></span> <span data-ttu-id="9af11-105">Yapışır, Linux dağıtımına yerleşik olarak bulunan paket yöneticisinin harika bir alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="9af11-105">Snaps are a great alternative to the package manager built into your Linux distribution.</span></span> <span data-ttu-id="9af11-106">Bu makalede, [.net aracılığıyla .net](https://snapcraft.io/dotnet-sdk)'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9af11-106">This article describes how to install .NET through [Snap](https://snapcraft.io/dotnet-sdk).</span></span>

<span data-ttu-id="9af11-107">Bir snap, bir uygulamanın bir paketidir ve farklı Linux dağıtımları arasında değişiklik yapılmaksızın, onun bağımlılıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="9af11-107">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="9af11-108">Yaslanabilirlik, ek depodan bulunabilir ve yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9af11-108">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="9af11-109">Yaslama hakkında daha fazla bilgi için bkz. [yaslama ile çalışmaya](https://snapcraft.io/docs/getting-started)başlama.</span><span class="sxs-lookup"><span data-stu-id="9af11-109">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

> [!CAUTION]
> <span data-ttu-id="9af11-110">Windows 10 ' da WSL2 'de yaslama paketleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9af11-110">Snap packages aren't supported in WSL2 on Windows 10.</span></span> <span data-ttu-id="9af11-111">Alternatif olarak, belirli bir WSL2 dağıtımı için [ `dotnet-install` betiği](linux-scripted-manual.md#scripted-install) veya paket yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9af11-111">As an alternative, use the [`dotnet-install` script](linux-scripted-manual.md#scripted-install) or the package manager for the particular WSL2 distribution.</span></span> <span data-ttu-id="9af11-112">Bu önerilmez, ancak anlık görüntü [forumlarından desteklenmeyen bir geçici çözümle](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)birlikte Yaslama özelliğini etkinleştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9af11-112">It's not recommended but you can try to enable snap with an [unsupported workaround from the snapcraft forums](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span></span>

## <a name="net-releases"></a><span data-ttu-id="9af11-113">.NET yayınları</span><span class="sxs-lookup"><span data-stu-id="9af11-113">.NET releases</span></span>

<span data-ttu-id="9af11-114">Yalnızca desteklenen .NET SDK sürümleri, Snap aracılığıyla kullanılabilir ✔️.</span><span class="sxs-lookup"><span data-stu-id="9af11-114">Only ✔️ supported versions of .NET SDK are available through Snap.</span></span> <span data-ttu-id="9af11-115">.NET çalışma zamanının tüm sürümleri, sürüm 2,1 ' den başlayarak ek olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9af11-115">All versions of the .NET Runtime are available through snap starting with version 2.1.</span></span> <span data-ttu-id="9af11-116">Aşağıdaki tabloda .NET (ve .NET Core) yayınları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="9af11-116">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="9af11-117">✔️ destekleniyor</span><span class="sxs-lookup"><span data-stu-id="9af11-117">✔️ Supported</span></span> | <span data-ttu-id="9af11-118">❌ Desteklenen</span><span class="sxs-lookup"><span data-stu-id="9af11-118">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="9af11-119">5.0</span><span class="sxs-lookup"><span data-stu-id="9af11-119">5.0</span></span>         | <span data-ttu-id="9af11-120">3,0</span><span class="sxs-lookup"><span data-stu-id="9af11-120">3.0</span></span>           |
| <span data-ttu-id="9af11-121">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="9af11-121">3.1 (LTS)</span></span>   | <span data-ttu-id="9af11-122">2.2</span><span class="sxs-lookup"><span data-stu-id="9af11-122">2.2</span></span>           |
| <span data-ttu-id="9af11-123">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="9af11-123">2.1 (LTS)</span></span>   | <span data-ttu-id="9af11-124">2.0</span><span class="sxs-lookup"><span data-stu-id="9af11-124">2.0</span></span>           |
|             | <span data-ttu-id="9af11-125">1.1</span><span class="sxs-lookup"><span data-stu-id="9af11-125">1.1</span></span>           |
|             | <span data-ttu-id="9af11-126">1,0</span><span class="sxs-lookup"><span data-stu-id="9af11-126">1.0</span></span>           |

<span data-ttu-id="9af11-127">.NET sürümlerinin yaşam döngüsü hakkında daha fazla bilgi için bkz. [.NET Core ve .NET 5 destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="9af11-127">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="sdk-or-runtime"></a><span data-ttu-id="9af11-128">SDK veya çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="9af11-128">SDK or Runtime</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a><span data-ttu-id="9af11-129">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="9af11-129">Install the SDK</span></span>

<span data-ttu-id="9af11-130">.NET SDK için Yaslama paketleri aynı tanımlayıcı altında yayımlanır: `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="9af11-130">Snap packages for the .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="9af11-131">Belirli bir SDK sürümü kanal belirtilerek yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9af11-131">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="9af11-132">SDK ilgili çalışma zamanını içerir.</span><span class="sxs-lookup"><span data-stu-id="9af11-132">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="9af11-133">Aşağıdaki tabloda kanallar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="9af11-133">The following table lists the channels:</span></span>

| <span data-ttu-id="9af11-134">.NET sürümü</span><span class="sxs-lookup"><span data-stu-id="9af11-134">.NET version</span></span> | <span data-ttu-id="9af11-135">Paket veya kanala yapışma</span><span class="sxs-lookup"><span data-stu-id="9af11-135">Snap package or channel</span></span>  |
|--------------|--------------------------|
| <span data-ttu-id="9af11-136">5.0</span><span class="sxs-lookup"><span data-stu-id="9af11-136">5.0</span></span>          | <span data-ttu-id="9af11-137">`5.0` veya `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="9af11-137">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="9af11-138">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="9af11-138">3.1 (LTS)</span></span>    | <span data-ttu-id="9af11-139">`3.1` veya `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="9af11-139">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="9af11-140">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="9af11-140">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="9af11-141">`snap install`.NET SDK Snap paketini yüklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9af11-141">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="9af11-142">`--channel`Hangi sürümün yükleneceğini belirtmek için parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9af11-142">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="9af11-143">Bu parametre atlanırsa, `latest/stable` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9af11-143">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="9af11-144">Bu örnekte, `5.0` belirtilir:</span><span class="sxs-lookup"><span data-stu-id="9af11-144">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="9af11-145">Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:</span><span class="sxs-lookup"><span data-stu-id="9af11-145">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="9af11-146">Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="9af11-146">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="9af11-147">İstediğiniz `{alias}` adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9af11-147">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="9af11-148">Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-sdk.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="9af11-148">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="9af11-149">Komutunu kullandığınızda `dotnet50` , .net 'in bu belirli sürümünü çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="9af11-149">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="9af11-150">Ancak farklı bir diğer ad seçilmesi, bir komutun kullanılmasını bekledikleri için birçok öğretici ve örnek ile uyumsuzdur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="9af11-150">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be used.</span></span>

## <a name="install-the-runtime"></a><span data-ttu-id="9af11-151">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="9af11-151">Install the runtime</span></span>

<span data-ttu-id="9af11-152">.NET çalışma zamanı için Yaslama paketleri kendi paket tanımlayıcılarıyla yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="9af11-152">Snap packages for the .NET Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="9af11-153">Aşağıdaki tabloda paket tanımlayıcıları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="9af11-153">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="9af11-154">.NET sürümü</span><span class="sxs-lookup"><span data-stu-id="9af11-154">.NET version</span></span>      | <span data-ttu-id="9af11-155">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="9af11-155">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="9af11-156">5.0</span><span class="sxs-lookup"><span data-stu-id="9af11-156">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="9af11-157">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="9af11-157">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="9af11-158">3,0</span><span class="sxs-lookup"><span data-stu-id="9af11-158">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="9af11-159">2.2</span><span class="sxs-lookup"><span data-stu-id="9af11-159">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="9af11-160">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="9af11-160">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="9af11-161">`snap install`.NET çalışma zamanı Snap paketini yüklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9af11-161">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="9af11-162">Bu örnekte, .NET 5,0 yüklüdür:</span><span class="sxs-lookup"><span data-stu-id="9af11-162">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="9af11-163">Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:</span><span class="sxs-lookup"><span data-stu-id="9af11-163">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="9af11-164">Komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="9af11-164">The command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="9af11-165">İstediğiniz `{alias}` adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9af11-165">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="9af11-166">Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-runtime-50.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="9af11-166">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="9af11-167">Komutunu kullandığınızda `dotnet50` , .net 'in belirli bir sürümünü çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="9af11-167">When you use the command `dotnet50`, you'll invoke a specific version of .NET.</span></span> <span data-ttu-id="9af11-168">Ancak farklı bir diğer ad seçmek bir komutun kullanılabilir olmasını bekledikleri için birçok öğretici ve örnek ile uyumsuzdur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="9af11-168">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

## <a name="tlsssl-certificate-errors"></a><span data-ttu-id="9af11-169">TLS/SSL sertifikası hataları</span><span class="sxs-lookup"><span data-stu-id="9af11-169">TLS/SSL Certificate errors</span></span>

<span data-ttu-id="9af11-170">.NET yaslama aracılığıyla yüklendiğinde, bazı bilgisayarlarda .NET TLS/SSL sertifikaları bulunamamış olabilir ve şu sırada bir hata alabilirsiniz `restore` :</span><span class="sxs-lookup"><span data-stu-id="9af11-170">When .NET is installed through Snap, it's possible that on some distros the .NET TLS/SSL certificates may not be found and you may receive an error during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="9af11-171">Bu sorunu çözmek için birkaç ortam değişkeni ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="9af11-171">To resolve this problem, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="9af11-172">Sertifika konumu, bir konuma göre farklılık gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="9af11-172">The certificate location will vary by distro.</span></span> <span data-ttu-id="9af11-173">İşte sorun yaşanmış olan yemekler için Konumlar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="9af11-173">Here are the locations for the distros where the issue has been experienced.</span></span>

| <span data-ttu-id="9af11-174">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="9af11-174">Distribution</span></span> | <span data-ttu-id="9af11-175">Konum</span><span class="sxs-lookup"><span data-stu-id="9af11-175">Location</span></span>                                            |
|--------------|-----------------------------------------------------|
| <span data-ttu-id="9af11-176">**Fedora**</span><span class="sxs-lookup"><span data-stu-id="9af11-176">**Fedora**</span></span>   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| <span data-ttu-id="9af11-177">**OpenSUSE**</span><span class="sxs-lookup"><span data-stu-id="9af11-177">**OpenSUSE**</span></span> | `/etc/ssl/ca-bundle.pem`                            |
| <span data-ttu-id="9af11-178">**Solus**</span><span class="sxs-lookup"><span data-stu-id="9af11-178">**Solus**</span></span>    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a><span data-ttu-id="9af11-179">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9af11-179">Next steps</span></span>

- [<span data-ttu-id="9af11-180">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9af11-180">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="9af11-181">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9af11-181">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)

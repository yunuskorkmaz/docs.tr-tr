---
title: Linux 'ta .NET 'i Snap-.NET ile yükler
description: Linux 'ta .NET SDK veya .NET çalışma zamanının yaslama ile nasıl yükleneceğini gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 0d91f5049c92df240e2c3e26bc67952abe17fedc
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190105"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a><span data-ttu-id="8cf41-103">.NET SDK veya .NET çalışma zamanını yaslama ile birlikte yükler</span><span class="sxs-lookup"><span data-stu-id="8cf41-103">Install the .NET SDK or the .NET Runtime with Snap</span></span>

<span data-ttu-id="8cf41-104">.NET SDK veya .NET çalışma zamanı yüklemek için bir snap paketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cf41-104">Use a Snap package to install the .NET SDK or .NET Runtime.</span></span> <span data-ttu-id="8cf41-105">Yapışır, Linux dağıtımına yerleşik olarak bulunan paket yöneticisinin harika bir alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="8cf41-105">Snaps are a great alternative to the package manager built into your Linux distribution.</span></span> <span data-ttu-id="8cf41-106">Bu makalede, [.net aracılığıyla .net](https://snapcraft.io/dotnet-sdk)'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8cf41-106">This article describes how to install .NET through [Snap](https://snapcraft.io/dotnet-sdk).</span></span>

<span data-ttu-id="8cf41-107">Bir snap, bir uygulamanın bir paketidir ve farklı Linux dağıtımları arasında değişiklik yapılmaksızın, onun bağımlılıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="8cf41-107">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="8cf41-108">Yaslanabilirlik, ek depodan bulunabilir ve yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8cf41-108">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="8cf41-109">Yaslama hakkında daha fazla bilgi için bkz. [yaslama ile çalışmaya](https://snapcraft.io/docs/getting-started)başlama.</span><span class="sxs-lookup"><span data-stu-id="8cf41-109">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

> [!CAUTION]
> <span data-ttu-id="8cf41-110">Windows 10 ' da WSL2 'de yaslama paketleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8cf41-110">Snap packages aren't supported in WSL2 on Windows 10.</span></span> <span data-ttu-id="8cf41-111">Alternatif olarak, belirli bir WSL2 dağıtımı için [ `dotnet-install` betiği](linux-scripted-manual.md#scripted-install) veya paket yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cf41-111">As an alternative, use the [`dotnet-install` script](linux-scripted-manual.md#scripted-install) or the package manager for the particular WSL2 distribution.</span></span> <span data-ttu-id="8cf41-112">Bu önerilmez, ancak anlık görüntü [forumlarından desteklenmeyen bir geçici çözümle](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)birlikte Yaslama özelliğini etkinleştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cf41-112">It's not recommended but you can try to enable snap with an [unsupported workaround from the snapcraft forums](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span></span>

## <a name="net-releases"></a><span data-ttu-id="8cf41-113">.NET yayınları</span><span class="sxs-lookup"><span data-stu-id="8cf41-113">.NET releases</span></span>

<span data-ttu-id="8cf41-114">Yalnızca desteklenen .NET SDK sürümleri, Snap aracılığıyla kullanılabilir ✔️.</span><span class="sxs-lookup"><span data-stu-id="8cf41-114">Only ✔️ supported versions of .NET SDK are available through Snap.</span></span> <span data-ttu-id="8cf41-115">.NET çalışma zamanının tüm sürümleri, sürüm 2,1 ' den başlayarak ek olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8cf41-115">All versions of the .NET Runtime are available through snap starting with version 2.1.</span></span> <span data-ttu-id="8cf41-116">Aşağıdaki tabloda .NET (ve .NET Core) yayınları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="8cf41-116">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="8cf41-117">✔️ destekleniyor</span><span class="sxs-lookup"><span data-stu-id="8cf41-117">✔️ Supported</span></span> | <span data-ttu-id="8cf41-118">❌ Desteklenen</span><span class="sxs-lookup"><span data-stu-id="8cf41-118">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="8cf41-119">5.0</span><span class="sxs-lookup"><span data-stu-id="8cf41-119">5.0</span></span>         | <span data-ttu-id="8cf41-120">3.0</span><span class="sxs-lookup"><span data-stu-id="8cf41-120">3.0</span></span>           |
| <span data-ttu-id="8cf41-121">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8cf41-121">3.1 (LTS)</span></span>   | <span data-ttu-id="8cf41-122">2,2</span><span class="sxs-lookup"><span data-stu-id="8cf41-122">2.2</span></span>           |
| <span data-ttu-id="8cf41-123">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8cf41-123">2.1 (LTS)</span></span>   | <span data-ttu-id="8cf41-124">2.0</span><span class="sxs-lookup"><span data-stu-id="8cf41-124">2.0</span></span>           |
|             | <span data-ttu-id="8cf41-125">1.1</span><span class="sxs-lookup"><span data-stu-id="8cf41-125">1.1</span></span>           |
|             | <span data-ttu-id="8cf41-126">1.0</span><span class="sxs-lookup"><span data-stu-id="8cf41-126">1.0</span></span>           |

<span data-ttu-id="8cf41-127">.NET sürümlerinin yaşam döngüsü hakkında daha fazla bilgi için bkz. [.NET Core ve .NET 5 destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="8cf41-127">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="sdk-or-runtime"></a><span data-ttu-id="8cf41-128">SDK veya çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8cf41-128">SDK or Runtime</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a><span data-ttu-id="8cf41-129">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="8cf41-129">Install the SDK</span></span>

<span data-ttu-id="8cf41-130">.NET SDK için Yaslama paketleri aynı tanımlayıcı altında yayımlanır: `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-130">Snap packages for the .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="8cf41-131">Belirli bir SDK sürümü kanal belirtilerek yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8cf41-131">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="8cf41-132">SDK ilgili çalışma zamanını içerir.</span><span class="sxs-lookup"><span data-stu-id="8cf41-132">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="8cf41-133">Aşağıdaki tabloda kanallar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="8cf41-133">The following table lists the channels:</span></span>

| <span data-ttu-id="8cf41-134">.NET sürümü</span><span class="sxs-lookup"><span data-stu-id="8cf41-134">.NET version</span></span> | <span data-ttu-id="8cf41-135">Paket veya kanala yapışma</span><span class="sxs-lookup"><span data-stu-id="8cf41-135">Snap package or channel</span></span>  |
|--------------|--------------------------|
| <span data-ttu-id="8cf41-136">5.0</span><span class="sxs-lookup"><span data-stu-id="8cf41-136">5.0</span></span>          | <span data-ttu-id="8cf41-137">`5.0` veya `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="8cf41-137">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="8cf41-138">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8cf41-138">3.1 (LTS)</span></span>    | <span data-ttu-id="8cf41-139">`3.1` veya `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="8cf41-139">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="8cf41-140">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8cf41-140">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="8cf41-141">`snap install`.NET SDK Snap paketini yüklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cf41-141">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="8cf41-142">`--channel`Hangi sürümün yükleneceğini belirtmek için parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cf41-142">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="8cf41-143">Bu parametre atlanırsa, `latest/stable` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8cf41-143">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="8cf41-144">Bu örnekte, `5.0` belirtilir:</span><span class="sxs-lookup"><span data-stu-id="8cf41-144">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="8cf41-145">Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:</span><span class="sxs-lookup"><span data-stu-id="8cf41-145">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="8cf41-146">Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-146">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="8cf41-147">İstediğiniz `{alias}` adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cf41-147">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="8cf41-148">Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-sdk.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-148">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="8cf41-149">Komutunu kullandığınızda `dotnet50` , .net 'in bu belirli sürümünü çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="8cf41-149">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="8cf41-150">Ancak farklı bir diğer ad seçilmesi, bir komutun kullanılmasını bekledikleri için birçok öğretici ve örnek ile uyumsuzdur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-150">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be used.</span></span>

## <a name="install-the-runtime"></a><span data-ttu-id="8cf41-151">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="8cf41-151">Install the runtime</span></span>

<span data-ttu-id="8cf41-152">.NET çalışma zamanı için Yaslama paketleri kendi paket tanımlayıcılarıyla yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="8cf41-152">Snap packages for the .NET Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="8cf41-153">Aşağıdaki tabloda paket tanımlayıcıları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="8cf41-153">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="8cf41-154">.NET sürümü</span><span class="sxs-lookup"><span data-stu-id="8cf41-154">.NET version</span></span>      | <span data-ttu-id="8cf41-155">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="8cf41-155">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="8cf41-156">5.0</span><span class="sxs-lookup"><span data-stu-id="8cf41-156">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="8cf41-157">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8cf41-157">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="8cf41-158">3.0</span><span class="sxs-lookup"><span data-stu-id="8cf41-158">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="8cf41-159">2,2</span><span class="sxs-lookup"><span data-stu-id="8cf41-159">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="8cf41-160">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8cf41-160">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="8cf41-161">`snap install`.NET çalışma zamanı Snap paketini yüklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cf41-161">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="8cf41-162">Bu örnekte, .NET 5,0 yüklüdür:</span><span class="sxs-lookup"><span data-stu-id="8cf41-162">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="8cf41-163">Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:</span><span class="sxs-lookup"><span data-stu-id="8cf41-163">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="8cf41-164">Komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-164">The command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="8cf41-165">İstediğiniz `{alias}` adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cf41-165">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="8cf41-166">Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-runtime-50.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-166">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="8cf41-167">Komutunu kullandığınızda `dotnet50` , .net 'in belirli bir sürümünü çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="8cf41-167">When you use the command `dotnet50`, you'll invoke a specific version of .NET.</span></span> <span data-ttu-id="8cf41-168">Ancak farklı bir diğer ad seçmek bir komutun kullanılabilir olmasını bekledikleri için birçok öğretici ve örnek ile uyumsuzdur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-168">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

## <a name="export-the-install-location"></a><span data-ttu-id="8cf41-169">Yüklemesi konumunu dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="8cf41-169">Export the install location</span></span>

<span data-ttu-id="8cf41-170">`DOTNET_ROOT`Ortam değişkeni, genellikle .net 'in nerede yükleneceğini belirlemede araçlar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8cf41-170">The `DOTNET_ROOT` environment variable is often used by tools to determine where .NET is installed.</span></span> <span data-ttu-id="8cf41-171">.NET, Snap aracılığıyla yüklendiğinde bu ortam değişkeni yapılandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="8cf41-171">When .NET is installed through Snap, this environment variable isn't configured.</span></span> <span data-ttu-id="8cf41-172">Profilinizde *DOTNET_ROOT* ortam değişkenini yapılandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8cf41-172">You should configure the *DOTNET_ROOT* environment variable in your profile.</span></span> <span data-ttu-id="8cf41-173">Yaslama yolu şu biçimi kullanır: `/snap/{package}/current` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-173">The path to the snap uses the following format: `/snap/{package}/current`.</span></span> <span data-ttu-id="8cf41-174">Örneğin, yaslama 'yı yüklediyseniz `dotnet-sdk` , ortam değişkenini .NET bulunduğu yere ayarlamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8cf41-174">For example, if you installed the `dotnet-sdk` snap, use the following command to set the environment variable to where .NET is located:</span></span>

```bash
export DOTNET_ROOT=/snap/dotnet-sdk/current
```

> [!TIP]
> <span data-ttu-id="8cf41-175">Yukarıdaki `export` komut yalnızca çalıştırıldığı terminal oturumu için ortam değişkenini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8cf41-175">The preceding `export` command only sets the environment variable for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="8cf41-176">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cf41-176">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="8cf41-177">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="8cf41-177">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="8cf41-178">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8cf41-178">For example:</span></span>
>
> - <span data-ttu-id="8cf41-179">**Bash kabuğu**: *~/.bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="8cf41-179">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="8cf41-180">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="8cf41-180">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="8cf41-181">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="8cf41-181">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="8cf41-182">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve ekleyin `export DOTNET_ROOT=/snap/dotnet-sdk/current` .</span><span class="sxs-lookup"><span data-stu-id="8cf41-182">Edit the appropriate source file for your shell and add `export DOTNET_ROOT=/snap/dotnet-sdk/current`.</span></span>

## <a name="tlsssl-certificate-errors"></a><span data-ttu-id="8cf41-183">TLS/SSL sertifikası hataları</span><span class="sxs-lookup"><span data-stu-id="8cf41-183">TLS/SSL Certificate errors</span></span>

<span data-ttu-id="8cf41-184">.NET yaslama aracılığıyla yüklendiğinde, bazı bilgisayarlarda .NET TLS/SSL sertifikaları bulunamamış olabilir ve şu sırada bir hata alabilirsiniz `restore` :</span><span class="sxs-lookup"><span data-stu-id="8cf41-184">When .NET is installed through Snap, it's possible that on some distros the .NET TLS/SSL certificates may not be found and you may receive an error during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="8cf41-185">Bu sorunu çözmek için birkaç ortam değişkeni ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8cf41-185">To resolve this problem, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="8cf41-186">Sertifika konumu, bir konuma göre farklılık gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="8cf41-186">The certificate location will vary by distro.</span></span> <span data-ttu-id="8cf41-187">İşte sorun yaşanmış olan yemekler için Konumlar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="8cf41-187">Here are the locations for the distros where the issue has been experienced.</span></span>

| <span data-ttu-id="8cf41-188">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="8cf41-188">Distribution</span></span> | <span data-ttu-id="8cf41-189">Konum</span><span class="sxs-lookup"><span data-stu-id="8cf41-189">Location</span></span>                                            |
|--------------|-----------------------------------------------------|
| <span data-ttu-id="8cf41-190">**Fedora**</span><span class="sxs-lookup"><span data-stu-id="8cf41-190">**Fedora**</span></span>   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| <span data-ttu-id="8cf41-191">**OpenSUSE**</span><span class="sxs-lookup"><span data-stu-id="8cf41-191">**OpenSUSE**</span></span> | `/etc/ssl/ca-bundle.pem`                            |
| <span data-ttu-id="8cf41-192">**Solus**</span><span class="sxs-lookup"><span data-stu-id="8cf41-192">**Solus**</span></span>    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a><span data-ttu-id="8cf41-193">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8cf41-193">Next steps</span></span>

- [<span data-ttu-id="8cf41-194">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8cf41-194">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="8cf41-195">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8cf41-195">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)

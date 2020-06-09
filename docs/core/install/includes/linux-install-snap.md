---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602917"
---

[<span data-ttu-id="d625b-101">.NET Core, Snap Store 'da bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d625b-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="d625b-102">Bir snap, bir uygulamanın bir paketidir ve farklı Linux dağıtımları arasında değişiklik yapılmaksızın, onun bağımlılıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="d625b-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="d625b-103">Yaslanabilirlik, ek depodan bulunabilir ve yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d625b-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="d625b-104">Yaslama hakkında daha fazla bilgi için bkz. [yaslama ile çalışmaya](https://snapcraft.io/docs/getting-started)başlama.</span><span class="sxs-lookup"><span data-stu-id="d625b-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="d625b-105">Yalnızca .NET Core 'un desteklenen sürümleri yaslama aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d625b-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="d625b-106">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="d625b-106">Install the SDK</span></span>

<span data-ttu-id="d625b-107">.NET Core SDK için Yaslama paketleri aynı tanımlayıcı altında yayımlanır: `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="d625b-107">Snap packages for .NET Core SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="d625b-108">Belirli bir SDK sürümü kanal belirtilerek yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d625b-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="d625b-109">SDK, birlikte yanıt verme çalışma zamanını içerir.</span><span class="sxs-lookup"><span data-stu-id="d625b-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="d625b-110">Aşağıdaki tabloda kanallar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d625b-110">The following table list the channels:</span></span>

| <span data-ttu-id="d625b-111">.NET Core sürümü</span><span class="sxs-lookup"><span data-stu-id="d625b-111">.NET Core version</span></span> | <span data-ttu-id="d625b-112">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="d625b-112">Snap package</span></span>             |
|-------------------|--------------------------|
| <span data-ttu-id="d625b-113">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="d625b-113">3.1 (LTS)</span></span>         | <span data-ttu-id="d625b-114">`3.1` veya `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="d625b-114">`3.1` or `latest/stable`</span></span> |
| <span data-ttu-id="d625b-115">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="d625b-115">2.1 (LTS)</span></span>         | `2.1`                    |
| <span data-ttu-id="d625b-116">.NET 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="d625b-116">.NET 5.0 preview</span></span>  | `5.0/beta`               |

<span data-ttu-id="d625b-117">`snap install`.NET Core SDK bir snap paketi yüklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d625b-117">Use the `snap install` command to install a .NET Core SDK snap package.</span></span> <span data-ttu-id="d625b-118">`--channel`Hangi sürümün yükleneceğini belirtmek için parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d625b-118">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="d625b-119">Bu parametre atlanırsa, `latest/stable` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d625b-119">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="d625b-120">Bu örnekte, `3.1` belirtilir:</span><span class="sxs-lookup"><span data-stu-id="d625b-120">In this example, `3.1` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

<span data-ttu-id="d625b-121">Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:</span><span class="sxs-lookup"><span data-stu-id="d625b-121">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="d625b-122">Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="d625b-122">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="d625b-123">İstediğiniz `{alias}` adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d625b-123">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="d625b-124">Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-sdk.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="d625b-124">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet31`.</span></span> <span data-ttu-id="d625b-125">Komutunu kullandığınızda `dotnet31` , .net 'in bu belirli sürümünü çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="d625b-125">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="d625b-126">Ancak bu, bir komutun kullanılabilir olmasını bekledikleri için çoğu öğretici ve örneklerle uyumsuzdur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="d625b-126">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="d625b-127">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="d625b-127">Install the runtime</span></span>

<span data-ttu-id="d625b-128">.NET Core çalışma zamanı için yapışma paketleri her biri kendi paket tanımlayıcılarıyla yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="d625b-128">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="d625b-129">Aşağıdaki tabloda paket tanımlayıcıları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d625b-129">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="d625b-130">.NET Core sürümü</span><span class="sxs-lookup"><span data-stu-id="d625b-130">.NET Core version</span></span> | <span data-ttu-id="d625b-131">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="d625b-131">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="d625b-132">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="d625b-132">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="d625b-133">3.0</span><span class="sxs-lookup"><span data-stu-id="d625b-133">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="d625b-134">2,2</span><span class="sxs-lookup"><span data-stu-id="d625b-134">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="d625b-135">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="d625b-135">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="d625b-136">`snap install`.NET Core çalışma zamanı ek paketi yüklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d625b-136">Use the `snap install` command to install a .NET Core Runtime snap package.</span></span> <span data-ttu-id="d625b-137">Bu örnekte, .NET Core 3,1 yüklüdür:</span><span class="sxs-lookup"><span data-stu-id="d625b-137">In this example, .NET Core 3.1 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-31 --classic
```

<span data-ttu-id="d625b-138">Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:</span><span class="sxs-lookup"><span data-stu-id="d625b-138">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

<span data-ttu-id="d625b-139">Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="d625b-139">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="d625b-140">İstediğiniz `{alias}` adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d625b-140">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="d625b-141">Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-runtime-31.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="d625b-141">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31`.</span></span> <span data-ttu-id="d625b-142">Komutunu kullandığınızda `dotnet31` , .net 'in bu belirli sürümünü çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="d625b-142">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="d625b-143">Ancak bu, bir komutun kullanılabilir olmasını bekledikleri için çoğu öğretici ve örneklerle uyumsuzdur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="d625b-143">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="d625b-144">SSL sertifikası hataları</span><span class="sxs-lookup"><span data-stu-id="d625b-144">SSL Certificate errors</span></span>

<span data-ttu-id="d625b-145">.NET, Snap aracılığıyla yüklendiğinde, bazı bilgisayarlarda .NET SSL sertifikaları bulunamamış olabilir ve aşağıdakiler sırasında aşağıdakine benzer bir hata alabilirsiniz `restore` :</span><span class="sxs-lookup"><span data-stu-id="d625b-145">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="d625b-146">Bu sorunu çözmek için birkaç ortamınızı değişkeni ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="d625b-146">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="d625b-147">Sertifika konumu, bir konuma göre farklılık gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="d625b-147">The certificate location will vary by distro.</span></span> <span data-ttu-id="d625b-148">İşte bu, sorunla karşılaştiğimiz, distro 'lara için konumlar.</span><span class="sxs-lookup"><span data-stu-id="d625b-148">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="d625b-149">Fedora`/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="d625b-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="d625b-150">OpenSUSE`/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="d625b-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="d625b-151">Solus-`/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="d625b-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>

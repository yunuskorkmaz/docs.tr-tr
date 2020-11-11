---
ms.openlocfilehash: 4ab2fc0645f76870dead99b5f45eef763643fb27
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506907"
---

[<span data-ttu-id="8542e-101">.NET Core, Snap Store 'da bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="8542e-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="8542e-102">Bir snap, bir uygulamanın bir paketidir ve farklı Linux dağıtımları arasında değişiklik yapılmaksızın, onun bağımlılıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="8542e-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="8542e-103">Yaslanabilirlik, ek depodan bulunabilir ve yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8542e-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="8542e-104">Yaslama hakkında daha fazla bilgi için bkz. [yaslama ile çalışmaya](https://snapcraft.io/docs/getting-started)başlama.</span><span class="sxs-lookup"><span data-stu-id="8542e-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="8542e-105">Yalnızca .NET Core 'un desteklenen sürümleri yaslama aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8542e-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="8542e-106">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="8542e-106">Install the SDK</span></span>

<span data-ttu-id="8542e-107">.NET SDK için Yaslama paketleri aynı tanımlayıcı altında yayımlanır: `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="8542e-107">Snap packages for .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="8542e-108">Belirli bir SDK sürümü kanal belirtilerek yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8542e-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="8542e-109">SDK, birlikte yanıt verme çalışma zamanını içerir.</span><span class="sxs-lookup"><span data-stu-id="8542e-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="8542e-110">Aşağıdaki tabloda kanallar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="8542e-110">The following table list the channels:</span></span>

| <span data-ttu-id="8542e-111">.NET sürümü</span><span class="sxs-lookup"><span data-stu-id="8542e-111">.NET version</span></span> | <span data-ttu-id="8542e-112">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="8542e-112">Snap package</span></span>             |
|--------------|--------------------------|
| <span data-ttu-id="8542e-113">5.0</span><span class="sxs-lookup"><span data-stu-id="8542e-113">5.0</span></span>          | <span data-ttu-id="8542e-114">`5.0` veya `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="8542e-114">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="8542e-115">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8542e-115">3.1 (LTS)</span></span>    | <span data-ttu-id="8542e-116">`3.1` veya `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="8542e-116">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="8542e-117">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8542e-117">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="8542e-118">`snap install`.NET SDK Snap paketini yüklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8542e-118">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="8542e-119">`--channel`Hangi sürümün yükleneceğini belirtmek için parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8542e-119">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="8542e-120">Bu parametre atlanırsa, `latest/stable` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8542e-120">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="8542e-121">Bu örnekte, `5.0` belirtilir:</span><span class="sxs-lookup"><span data-stu-id="8542e-121">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="8542e-122">Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:</span><span class="sxs-lookup"><span data-stu-id="8542e-122">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="8542e-123">Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="8542e-123">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="8542e-124">İstediğiniz `{alias}` adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8542e-124">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="8542e-125">Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-sdk.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="8542e-125">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="8542e-126">Komutunu kullandığınızda `dotnet50` , .net 'in bu belirli sürümünü çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="8542e-126">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="8542e-127">Ancak bu, bir komutun kullanılabilir olmasını bekledikleri için çoğu öğretici ve örneklerle uyumsuzdur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="8542e-127">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="8542e-128">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="8542e-128">Install the runtime</span></span>

<span data-ttu-id="8542e-129">.NET Core çalışma zamanı için yapışma paketleri her biri kendi paket tanımlayıcılarıyla yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="8542e-129">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="8542e-130">Aşağıdaki tabloda paket tanımlayıcıları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="8542e-130">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="8542e-131">.NET sürümü</span><span class="sxs-lookup"><span data-stu-id="8542e-131">.NET version</span></span>      | <span data-ttu-id="8542e-132">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="8542e-132">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="8542e-133">5.0</span><span class="sxs-lookup"><span data-stu-id="8542e-133">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="8542e-134">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8542e-134">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="8542e-135">3,0</span><span class="sxs-lookup"><span data-stu-id="8542e-135">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="8542e-136">2.2</span><span class="sxs-lookup"><span data-stu-id="8542e-136">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="8542e-137">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="8542e-137">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="8542e-138">`snap install`.NET çalışma zamanı Snap paketini yüklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8542e-138">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="8542e-139">Bu örnekte, .NET 5,0 yüklüdür:</span><span class="sxs-lookup"><span data-stu-id="8542e-139">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="8542e-140">Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:</span><span class="sxs-lookup"><span data-stu-id="8542e-140">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="8542e-141">Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="8542e-141">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="8542e-142">İstediğiniz `{alias}` adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8542e-142">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="8542e-143">Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-runtime-50.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="8542e-143">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="8542e-144">Komutunu kullandığınızda `dotnet50` , .net 'in bu belirli sürümünü çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="8542e-144">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="8542e-145">Ancak bu, bir komutun kullanılabilir olmasını bekledikleri için çoğu öğretici ve örneklerle uyumsuzdur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="8542e-145">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="8542e-146">SSL sertifikası hataları</span><span class="sxs-lookup"><span data-stu-id="8542e-146">SSL Certificate errors</span></span>

<span data-ttu-id="8542e-147">.NET, Snap aracılığıyla yüklendiğinde, bazı bilgisayarlarda .NET SSL sertifikaları bulunamamış olabilir ve aşağıdakiler sırasında aşağıdakine benzer bir hata alabilirsiniz `restore` :</span><span class="sxs-lookup"><span data-stu-id="8542e-147">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="8542e-148">Bu sorunu çözmek için birkaç ortamınızı değişkeni ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8542e-148">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="8542e-149">Sertifika konumu, bir konuma göre farklılık gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="8542e-149">The certificate location will vary by distro.</span></span> <span data-ttu-id="8542e-150">İşte bu, sorunla karşılaştiğimiz, distro 'lara için konumlar.</span><span class="sxs-lookup"><span data-stu-id="8542e-150">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="8542e-151">Fedora `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="8542e-151">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="8542e-152">OpenSUSE `/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="8542e-152">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="8542e-153">Solus- `/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="8542e-153">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>

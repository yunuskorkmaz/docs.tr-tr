---
title: Linux 'ta .NET 'i el ile yükler-.NET
description: Linux üzerinde bir paket yöneticisi olmadan .NET SDK ve .NET çalışma zamanının nasıl yükleneceğini gösterir. Install betiğini kullanın veya ikili dosyaları el ile ayıklayın.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6840814627be0124d7b3855f08a433eab76eac4a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873919"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a><span data-ttu-id="eff87-104">.NET SDK veya .NET çalışma zamanını el ile yükleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="eff87-104">Install the .NET SDK or the .NET Runtime manually</span></span>

<span data-ttu-id="eff87-105">.NET, Linux üzerinde desteklenmektedir ve bu makalede, Install betiği kullanılarak veya ikili dosyaları ayıklanarak Linux 'ta .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="eff87-105">.NET is supported on Linux and this article describes how to install .NET on Linux using the install script or by extracting the binaries.</span></span> <span data-ttu-id="eff87-106">Yerleşik paket yöneticisini destekleyen dağıtımların bir listesi için bkz. [Linux 'ta .net 'ı Install](linux.md).</span><span class="sxs-lookup"><span data-stu-id="eff87-106">For a list of distributions that support the built-in package manager, see [Install .NET on Linux](linux.md).</span></span>

<span data-ttu-id="eff87-107">Ayrıca, yaslama ile .NET yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eff87-107">You can also install .NET with snap.</span></span> <span data-ttu-id="eff87-108">Daha fazla bilgi için bkz. [.NET SDK 'yı veya .NET çalışma zamanını yaslama Ile yüklemeyi](linux-snap.md).</span><span class="sxs-lookup"><span data-stu-id="eff87-108">For more information, see [Install the .NET SDK or the .NET Runtime with Snap](linux-snap.md).</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a><span data-ttu-id="eff87-109">.NET yayınları</span><span class="sxs-lookup"><span data-stu-id="eff87-109">.NET releases</span></span>

<span data-ttu-id="eff87-110">Aşağıdaki tabloda .NET (ve .NET Core) yayınları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="eff87-110">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="eff87-111">✔️ destekleniyor</span><span class="sxs-lookup"><span data-stu-id="eff87-111">✔️ Supported</span></span> | <span data-ttu-id="eff87-112">❌ Desteklenen</span><span class="sxs-lookup"><span data-stu-id="eff87-112">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="eff87-113">5.0</span><span class="sxs-lookup"><span data-stu-id="eff87-113">5.0</span></span>         | <span data-ttu-id="eff87-114">3.0</span><span class="sxs-lookup"><span data-stu-id="eff87-114">3.0</span></span>           |
| <span data-ttu-id="eff87-115">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="eff87-115">3.1 (LTS)</span></span>   | <span data-ttu-id="eff87-116">2,2</span><span class="sxs-lookup"><span data-stu-id="eff87-116">2.2</span></span>           |
| <span data-ttu-id="eff87-117">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="eff87-117">2.1 (LTS)</span></span>   | <span data-ttu-id="eff87-118">2.0</span><span class="sxs-lookup"><span data-stu-id="eff87-118">2.0</span></span>           |
|             | <span data-ttu-id="eff87-119">1.1</span><span class="sxs-lookup"><span data-stu-id="eff87-119">1.1</span></span>           |
|             | <span data-ttu-id="eff87-120">1.0</span><span class="sxs-lookup"><span data-stu-id="eff87-120">1.0</span></span>           |

<span data-ttu-id="eff87-121">.NET sürümlerinin yaşam döngüsü hakkında daha fazla bilgi için bkz. [.NET Core ve .NET 5 destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="eff87-121">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="dependencies"></a><span data-ttu-id="eff87-122">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="eff87-122">Dependencies</span></span>

<span data-ttu-id="eff87-123">.NET yüklediğinizde belirli bağımlılıklar yüklenemeyebilir, örneğin [el ile yüklenirken](#manual-install).</span><span class="sxs-lookup"><span data-stu-id="eff87-123">It's possible that when you install .NET, specific dependencies may not be installed, such as when [manually installing](#manual-install).</span></span> <span data-ttu-id="eff87-124">Aşağıdaki listede, Microsoft tarafından desteklenen ve yüklemeniz gerekebilecek bağımlılıklara sahip Linux dağıtımlarını ayrıntılarıyla bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eff87-124">The following list details Linux distributions that are supported by Microsoft and have dependencies you may need to install.</span></span> <span data-ttu-id="eff87-125">Daha fazla bilgi için dağıtım sayfasına bakın:</span><span class="sxs-lookup"><span data-stu-id="eff87-125">Check the distribution page for more information:</span></span>

- [<span data-ttu-id="eff87-126">Alpine</span><span class="sxs-lookup"><span data-stu-id="eff87-126">Alpine</span></span>](linux-alpine.md#dependencies)
- [<span data-ttu-id="eff87-127">Debian</span><span class="sxs-lookup"><span data-stu-id="eff87-127">Debian</span></span>](linux-debian.md#dependencies)
- [<span data-ttu-id="eff87-128">CentOS</span><span class="sxs-lookup"><span data-stu-id="eff87-128">CentOS</span></span>](linux-centos.md#dependencies)
- [<span data-ttu-id="eff87-129">Fedora</span><span class="sxs-lookup"><span data-stu-id="eff87-129">Fedora</span></span>](linux-fedora.md#dependencies)
- [<span data-ttu-id="eff87-130">RHEL</span><span class="sxs-lookup"><span data-stu-id="eff87-130">RHEL</span></span>](linux-rhel.md#dependencies)
- [<span data-ttu-id="eff87-131">SLES</span><span class="sxs-lookup"><span data-stu-id="eff87-131">SLES</span></span>](linux-sles.md#dependencies)
- [<span data-ttu-id="eff87-132">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="eff87-132">Ubuntu</span></span>](linux-ubuntu.md#dependencies)

<span data-ttu-id="eff87-133">Bağımlılıklar hakkında genel bilgi için bkz. [kendi kendine kapsanan Linux uygulamaları](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="eff87-133">For generic information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span></span>

### <a name="rpm-dependencies"></a><span data-ttu-id="eff87-134">RPM bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="eff87-134">RPM dependencies</span></span>

<span data-ttu-id="eff87-135">Dağıtım daha önce listelenmediyse ve RPM tabanlı ise, Aşağıdaki bağımlılıklara ihtiyacınız olabilir:</span><span class="sxs-lookup"><span data-stu-id="eff87-135">If your distribution wasn't previously listed, and is RPM-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="eff87-136">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="eff87-136">krb5-libs</span></span>
- <span data-ttu-id="eff87-137">libıu</span><span class="sxs-lookup"><span data-stu-id="eff87-137">libicu</span></span>
- <span data-ttu-id="eff87-138">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="eff87-138">openssl-libs</span></span>

<span data-ttu-id="eff87-139">Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10** yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eff87-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

### <a name="deb-dependencies"></a><span data-ttu-id="eff87-140">DEB bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="eff87-140">DEB dependencies</span></span>

<span data-ttu-id="eff87-141">Dağıtım daha önce listelenmediyse ve temel alıyorsa, Aşağıdaki bağımlılıklara ihtiyacınız olabilir:</span><span class="sxs-lookup"><span data-stu-id="eff87-141">If your distribution wasn't previously listed, and is debian-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="eff87-142">libc6</span><span class="sxs-lookup"><span data-stu-id="eff87-142">libc6</span></span>
- <span data-ttu-id="eff87-143">libgcc1</span><span class="sxs-lookup"><span data-stu-id="eff87-143">libgcc1</span></span>
- <span data-ttu-id="eff87-144">libgssapı-krb5-2</span><span class="sxs-lookup"><span data-stu-id="eff87-144">libgssapi-krb5-2</span></span>
- <span data-ttu-id="eff87-145">libicu67</span><span class="sxs-lookup"><span data-stu-id="eff87-145">libicu67</span></span>
- <span data-ttu-id="eff87-146">libssl 1.1</span><span class="sxs-lookup"><span data-stu-id="eff87-146">libssl1.1</span></span>
- <span data-ttu-id="eff87-147">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="eff87-147">libstdc++6</span></span>
- <span data-ttu-id="eff87-148">zlib1g</span><span class="sxs-lookup"><span data-stu-id="eff87-148">zlib1g</span></span>

### <a name="common-dependencies"></a><span data-ttu-id="eff87-149">Ortak bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="eff87-149">Common dependencies</span></span>

<span data-ttu-id="eff87-150">*System. Drawing. Common* derlemesini kullanan .NET uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="eff87-150">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="eff87-151">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="eff87-151">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="eff87-152">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eff87-152">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="eff87-153">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="eff87-153">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="eff87-154">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="eff87-154">Scripted install</span></span>

<span data-ttu-id="eff87-155">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , **SDK** ve **çalışma zamanının** Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eff87-155">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="eff87-156">Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .</span><span class="sxs-lookup"><span data-stu-id="eff87-156">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="eff87-157">Komut dosyası, .NET Core 3,1 olan en son SDK [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eff87-157">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="eff87-158">(LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eff87-158">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="eff87-159">SDK yerine .NET Runtime yüklemek için `--runtime` parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eff87-159">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="eff87-160">Belirli sürümü göstermek için parametresini değiştirerek belirli bir sürümü yükleyebilirsiniz `-c` .</span><span class="sxs-lookup"><span data-stu-id="eff87-160">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="eff87-161">Aşağıdaki komut .NET SDK 5,0 'yi yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="eff87-161">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="eff87-162">Daha fazla bilgi için bkz. [DotNet-Install betikler Reference](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="eff87-162">For more information, see [dotnet-install scripts reference](../tools/dotnet-install-script.md).</span></span>

## <a name="manual-install"></a><span data-ttu-id="eff87-163">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="eff87-163">Manual install</span></span>

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="eff87-164">Paket yöneticilerine alternatif olarak SDK ve çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eff87-164">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="eff87-165">El ile yüklemesi, genellikle sürekli tümleştirme testinin parçası olarak veya desteklenmeyen bir Linux dağıtımında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eff87-165">Manual install is commonly used as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="eff87-166">Bir geliştirici veya Kullanıcı için bir paket yöneticisi kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="eff87-166">For a developer or user, it's better to use a package manager.</span></span>

<span data-ttu-id="eff87-167">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eff87-167">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="eff87-168">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için **ikili** bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="eff87-168">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="eff87-169">✔️ [.net 5,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="eff87-169">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="eff87-170">✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/3.1)</span><span class="sxs-lookup"><span data-stu-id="eff87-170">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet/3.1)</span></span>
- <span data-ttu-id="eff87-171">✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/2.1)</span><span class="sxs-lookup"><span data-stu-id="eff87-171">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet/2.1)</span></span>
- [<span data-ttu-id="eff87-172">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="eff87-172">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet)

<span data-ttu-id="eff87-173">Ardından, indirilen dosyayı ayıklayın ve `export` .NET tarafından kullanılan değişkenleri ayarlamak için komutunu kullanın ve ardından .net 'ın yol içinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="eff87-173">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="eff87-174">Çalışma zamanını ayıklamak ve .NET CLı komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET ikili sürümü indirin.</span><span class="sxs-lookup"><span data-stu-id="eff87-174">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="eff87-175">Ardından, bir Terminal açın ve dosyanın kaydedildiği dizinden aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eff87-175">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="eff87-176">Arşiv dosyası adı, indirdiklerinize bağlı olarak farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="eff87-176">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="eff87-177">**İndirdiğiniz çalışma zamanını veya SDK 'Yı ayıklamak için aşağıdaki komutları kullanın.**</span><span class="sxs-lookup"><span data-stu-id="eff87-177">**Use the following commands to extract the runtime or SDK that you downloaded.**</span></span> <span data-ttu-id="eff87-178">`DOTNET_FILE`Değeri dosya adınızla değiştirmeyi unutmayın:</span><span class="sxs-lookup"><span data-stu-id="eff87-178">Remember to change the `DOTNET_FILE` value to your file name:</span></span>

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> <span data-ttu-id="eff87-179">Yukarıdaki `export` Komutlar yalnızca .net CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="eff87-179">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="eff87-180">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eff87-180">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="eff87-181">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="eff87-181">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="eff87-182">Örnek:</span><span class="sxs-lookup"><span data-stu-id="eff87-182">For example:</span></span>
>
> - <span data-ttu-id="eff87-183">**Bash kabuğu**: *~/.bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="eff87-183">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="eff87-184">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="eff87-184">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="eff87-185">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="eff87-185">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="eff87-186">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve `:$HOME/dotnet` var olan deyimin sonuna ekleyin `PATH` .</span><span class="sxs-lookup"><span data-stu-id="eff87-186">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="eff87-187">Hiçbir `PATH` ifade dahil yoksa, ile yeni bir satır ekleyin `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="eff87-187">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="eff87-188">Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eff87-188">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="eff87-189">Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="eff87-189">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="eff87-190">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="eff87-190">Next steps</span></span>

- [<span data-ttu-id="eff87-191">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="eff87-191">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="eff87-192">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="eff87-192">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)

---
title: .NET core genel araçları
description: .NET Core genel araçları nelerdir ve bunlar için kullanılabilen .NET Core CLI komutları genel bakış.
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697098"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="58546-103">.NET core genel araçlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="58546-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="58546-104">Bir .NET Core genel bir konsol uygulaması içeren özel bir NuGet paketi aracıdır.</span><span class="sxs-lookup"><span data-stu-id="58546-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="58546-105">Genel bir aracı makinenizde PATH ortam değişkeni bulunan bir varsayılan konum ya da özel bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="58546-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="58546-106">.NET Core genel aracı kullanmak istiyorsanız:</span><span class="sxs-lookup"><span data-stu-id="58546-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="58546-107">Aracı (genellikle bir Web sitesi veya GitHub sayfası) hakkında bilgiler bulun.</span><span class="sxs-lookup"><span data-stu-id="58546-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="58546-108">Yazar ve akış (genellikle NuGet.org) için Giriş İstatistikleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="58546-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="58546-109">Aracı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="58546-109">Install the tool.</span></span>
* <span data-ttu-id="58546-110">Aracı'nı arayın.</span><span class="sxs-lookup"><span data-stu-id="58546-110">Call the tool.</span></span>
* <span data-ttu-id="58546-111">Aracı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="58546-111">Update the tool.</span></span>
* <span data-ttu-id="58546-112">Aracı'nı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="58546-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="58546-113">.NET core genel araçları, yolunuza görünür ve tam güvende çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="58546-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="58546-114">Yazarın güvenmediğiniz sürece .NET Core genel araçları yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="58546-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="58546-115">.NET Core genel aracı Bul</span><span class="sxs-lookup"><span data-stu-id="58546-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="58546-116">Şu anda, .NET Core komut satırı arabirimi (CLI) bir genel aracı arama özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="58546-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="58546-117">.NET Core genel araçları bulabilirsiniz [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="58546-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="58546-118">Ancak, NuGet henüz özellikle .NET Core genel araçları için arama yapmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="58546-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="58546-119">Aracı önerilerinde blog gönderileri ya da buna ayrıca bulabilirsiniz [dotnet/natemcmaster-tools](https://github.com/natemcmaster/dotnet-tools) GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="58546-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="58546-120">Genel ASP.NET ekibi tarafından oluşturulan araçları için kaynak kodunu da görebilirsiniz [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="58546-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="58546-121">Yazar ve istatistikleri denetleyin</span><span class="sxs-lookup"><span data-stu-id="58546-121">Check the author and statistics</span></span>

<span data-ttu-id="58546-122">.NET Core genel araçları tam güvende çalıştırma ve genelde yol üzerinde yüklü olduğundan, bunlar çok güçlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="58546-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="58546-123">Araçlar güvenmediğiniz kişilerden yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="58546-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="58546-124">Aracı NuGet üzerinde barındırılıyorsa, aracı için arama yaparak yazar ve istatistikleri kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58546-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="58546-125">Genel bir aracı yükleyin</span><span class="sxs-lookup"><span data-stu-id="58546-125">Install a Global Tool</span></span>

<span data-ttu-id="58546-126">Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](dotnet-tool-install.md) .NET Core CLI komutu.</span><span class="sxs-lookup"><span data-stu-id="58546-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="58546-127">Aşağıdaki örnek bir genel aracın varsayılan konumda nasıl yükleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="58546-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="58546-128">Aracı yüklü değilse, hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="58546-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="58546-129">Beklediğiniz akışları teslim denetleyin.</span><span class="sxs-lookup"><span data-stu-id="58546-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="58546-130">Bir yayın öncesi sürüm veya aracı belirli bir sürümünü yüklemek çalışıyorsanız, aşağıdaki biçimi kullanarak sürüm numarasını belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58546-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="58546-131">Yükleme başarılı olursa, aracı ve yüklü sürüm çağırmak için kullanılan komut aşağıdaki örneğe benzer gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="58546-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="58546-132">Varsayılan dizini veya belirli bir konuma genel araçları yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="58546-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="58546-133">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="58546-133">The default directories are:</span></span>

| <span data-ttu-id="58546-134">İŞLETİM SİSTEMİ</span><span class="sxs-lookup"><span data-stu-id="58546-134">OS</span></span>          | <span data-ttu-id="58546-135">Yol</span><span class="sxs-lookup"><span data-stu-id="58546-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="58546-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="58546-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="58546-137">Windows</span><span class="sxs-lookup"><span data-stu-id="58546-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="58546-138">SDK'yı ilk kez çalıştırdığınızda, genel yüklü araçları doğrudan olarak adlandırılan şekilde bu konumları kullanıcının yoluna eklenir.</span><span class="sxs-lookup"><span data-stu-id="58546-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="58546-139">Genel araçları kullanıcıya özgü olduğuna dikkat edin, genel makine değil.</span><span class="sxs-lookup"><span data-stu-id="58546-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="58546-140">Makinenin tüm kullanıcıları için kullanılabilir olan bir genel aracı yükleyemezsiniz olan kullanıcıya özgü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="58546-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="58546-141">Aracı yalnızca, aracı yüklendiği her bir kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="58546-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="58546-142">Genel araçları Ayrıca belirli bir dizindeki yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="58546-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="58546-143">Belirli bir dizindeki yüklendiğinde kullanıcı komutu kullanılabiliyorsa, belirtilen dizinle komutu çağırarak yolunda bu dizine dahil ederek emin olmalısınız ya da belirtilen dizin içinde aracından çağırma.</span><span class="sxs-lookup"><span data-stu-id="58546-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="58546-144">Bu durumda, .NET Core CLI bu konuma otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="58546-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="58546-145">Aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="58546-145">Use the tool</span></span>

<span data-ttu-id="58546-146">Aracı yüklendikten sonra kendi komutunu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58546-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="58546-147">Komut paket adı ile aynı olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="58546-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="58546-148">Komut ise `dotnetsay`, kendisiyle çağırın:</span><span class="sxs-lookup"><span data-stu-id="58546-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="58546-149">Aracı Yazar bağlamında görünmesi aracı istedik varsa `dotnet` istemi, bunlar yazdığınız bu şekilde olarak çağrı `dotnet <command>`, gibi:</span><span class="sxs-lookup"><span data-stu-id="58546-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="58546-150">Hangi araçların bir yüklü genel aracını kullanarak yüklü paketleri listeleyerek paketinde bulunan bulabilirsiniz [dotnet araç listesi](dotnet-tool-list.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="58546-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="58546-151">Kullanım yönergeleri aracın Web sitesindeki ya da aşağıdaki komutlardan birini yazarak da arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58546-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="58546-152">Nerede sorun çıkabilir</span><span class="sxs-lookup"><span data-stu-id="58546-152">What could go wrong</span></span>

<span data-ttu-id="58546-153">Genel araçlardır [framework bağımlı uygulamaları](../deploying/index.md#framework-dependent-deployments-fdd), bunlar Bel makinenize yüklü bir .NET çekirdeği çalışma zamanı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="58546-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="58546-154">Beklenen çalışma zamanı bulunmazsa, bunlar gibi normal .NET çekirdeği çalışma zamanı İleri alma kurallarını uygulayın:</span><span class="sxs-lookup"><span data-stu-id="58546-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="58546-155">Bir uygulama belirtilen birincil ve ikincil sürüm en yüksek düzeltme sürümüne İleri yapar.</span><span class="sxs-lookup"><span data-stu-id="58546-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="58546-156">Bir ana eşleşen ve ikincil sürüm numarası ile eşleşen hiçbir çalışma zamanı sonraki daha yüksek alt sürüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58546-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="58546-157">İleri çalışma zamanı Önizleme sürümleri veya Önizleme ve yayın sürümleri arasında oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="58546-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="58546-158">Bu nedenle, genel Önizleme sürümleri kullanılarak oluşturulan araçları yeniden ve yazar tarafından yeniden yayımlanması ve gerekir yeniden.</span><span class="sxs-lookup"><span data-stu-id="58546-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="58546-159">Genel .NET Core 2.1 Preview 1'de oluşturulan araçları ile ek sorunlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="58546-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="58546-160">Daha fazla bilgi için bkz: [.NET Core 2.1 Preview 2 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="58546-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="58546-161">Bir uygulama uygun bir çalışma zamanı bulamazsanız, çalıştırmak başarısız olur ve bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="58546-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="58546-162">Bir önceki Önizleme sırasında oluşturulan bir genel aracı, şu anda yüklü .NET çekirdeği çalışma zamanları ile çalışmayabilir gerçekleşebilir başka bir sorun olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="58546-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="58546-163">Hangi çalışma zamanları makinenizde aşağıdaki komutu kullanarak yüklü olan görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58546-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="58546-164">Genel aracı yazarına başvurun ve bunlar derlenir ve güncelleştirilmiş sürüm numarası olan NuGet için kendi aracı paketi yeniden yayımlamanız varsa bkz.</span><span class="sxs-lookup"><span data-stu-id="58546-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="58546-165">NuGet paketi güncelleştirdikten sonra kopyanızı güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58546-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="58546-166">İlk kullanım üzerinde PATH ortam değişkeni varsayılan konumları eklemek .NET Core CLI çalışır.</span><span class="sxs-lookup"><span data-stu-id="58546-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="58546-167">Ancak, birkaç burada konumu değil eklenmesi YOLUNU otomatik olarak senaryo vardır gibi:</span><span class="sxs-lookup"><span data-stu-id="58546-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="58546-168">Ayarlamış olmanız `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="58546-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="58546-169">.NET Core SDK'sını kullanarak yüklediyseniz macOS üzerinde *. tar.gz* dosyaları ve *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="58546-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="58546-170">Linux üzerinde yolu yapılandırmak için kabuk ortam dosyasını düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="58546-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="58546-171">Diğer CLI komutları</span><span class="sxs-lookup"><span data-stu-id="58546-171">Other CLI commands</span></span>

<span data-ttu-id="58546-172">.NET Core SDK destek .NET Core genel araçları diğer komutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="58546-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="58546-173">Herhangi birini kullanan `dotnet tool` aşağıdaki seçeneklerden birini komutlarıyla:</span><span class="sxs-lookup"><span data-stu-id="58546-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="58546-174">`--global` veya `-g` komutu kullanıcı genelinde geçerli genel araçları olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="58546-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="58546-175">`--tool-path` özel bir konuma için genel araçları belirtir.</span><span class="sxs-lookup"><span data-stu-id="58546-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="58546-176">Öğrenmek için genel araçlar için hangi komutları kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="58546-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="58546-177">Genel bir aracı güncelleştirme kaldırıp en son kararlı sürümü ile yeniden yüklemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="58546-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="58546-178">Genel bir aracı güncelleştirmek için [dotnet aracı güncelleştirme](dotnet-tool-update.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="58546-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="58546-179">Genel aracını kullanarak kaldırma [dotnet Aracı kaldırma](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="58546-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="58546-180">Genel, sürüm ve komutları yanı sıra makine yüklü araçların tümünü görüntülemek için kullanın [dotnet araç listesi](dotnet-tool-list.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="58546-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```
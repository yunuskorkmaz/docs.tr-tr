---
title: .NET Core küresel araçları
description: .NET Core genel araçlarının ne olduğuna ve bunlara yönelik .NET Core CLI komutlarına genel bakış.
author: KathleenDollard
ms.date: 05/29/2018
ms.openlocfilehash: 1531df48b7ca9c816b897d06e725ec375f6cae31
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920500"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="8b56b-103">.NET Core genel araçlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="8b56b-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="8b56b-104">.NET Core küresel Aracı, konsol uygulaması içeren özel bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="8b56b-105">Bir genel araç, makinenizde, PATH ortam değişkenine veya özel bir konuma dahil olan varsayılan bir konumda yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="8b56b-106">.NET Core küresel aracı kullanmak istiyorsanız:</span><span class="sxs-lookup"><span data-stu-id="8b56b-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="8b56b-107">Araçla ilgili bilgileri bulun (genellikle bir Web sitesi veya GitHub sayfası).</span><span class="sxs-lookup"><span data-stu-id="8b56b-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="8b56b-108">Akışın giriş sayfasındaki yazar ve istatistikleri denetleyin (genellikle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="8b56b-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="8b56b-109">Aracı 'nı yükler.</span><span class="sxs-lookup"><span data-stu-id="8b56b-109">Install the tool.</span></span>
* <span data-ttu-id="8b56b-110">Aracı çağırın.</span><span class="sxs-lookup"><span data-stu-id="8b56b-110">Call the tool.</span></span>
* <span data-ttu-id="8b56b-111">Aracı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="8b56b-111">Update the tool.</span></span>
* <span data-ttu-id="8b56b-112">Aracı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8b56b-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b56b-113">.NET Core küresel araçları yolunuzda görünür ve tam güvende çalışır.</span><span class="sxs-lookup"><span data-stu-id="8b56b-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="8b56b-114">Yazara güvenmediğiniz .NET Core küresel araçlarını yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="8b56b-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="8b56b-115">.NET Core küresel aracı bulma</span><span class="sxs-lookup"><span data-stu-id="8b56b-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="8b56b-116">Şu anda .NET Core CLI genel bir araç arama özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b56b-116">Currently, there isn't a Global Tool search feature in the .NET Core CLI.</span></span> <span data-ttu-id="8b56b-117">Araçların nasıl bulunacağı hakkında bazı öneriler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b56b-117">The following are some recommendations on how to find tools:</span></span>

* <span data-ttu-id="8b56b-118">[NuGet](https://www.nuget.org)üzerinde .NET Core küresel araçları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b56b-118">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="8b56b-119">Ancak, NuGet henüz .NET Core küresel araçları için arama yapmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="8b56b-119">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>
* <span data-ttu-id="8b56b-120">Araç önerilerini blog gönderilerinde veya [natemcmaster/DotNet-Tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b56b-120">You may find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="8b56b-121">[DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) GitHub deposunda ASP.NET ekibi tarafından oluşturulan genel araçların kaynak kodunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b56b-121">You can see the source code for the Global Tools created by the ASP.NET team at the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) GitHub repository.</span></span>
* <span data-ttu-id="8b56b-122">[.NET Core DotNet Diagnostic küresel araçlar](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)' da tanılama araçları hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b56b-122">You can learn about diagnostic tools at [.NET Core dotnet diagnostic Global Tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="8b56b-123">Yazarı ve istatistikleri denetleme</span><span class="sxs-lookup"><span data-stu-id="8b56b-123">Check the author and statistics</span></span>

<span data-ttu-id="8b56b-124">.NET Core küresel araçları tam güvende çalıştığı ve genellikle yolunuza yüklendiği için, bu, çok güçlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-124">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="8b56b-125">Güvenmediğiniz kişilerden araç indirmeyin.</span><span class="sxs-lookup"><span data-stu-id="8b56b-125">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="8b56b-126">Araç NuGet üzerinde barındırılıyorsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b56b-126">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="8b56b-127">Küresel bir araç yükler</span><span class="sxs-lookup"><span data-stu-id="8b56b-127">Install a Global Tool</span></span>

<span data-ttu-id="8b56b-128">Küresel bir araç yüklemek için [DotNet aracı install](dotnet-tool-install.md) .NET Core CLI komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b56b-128">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="8b56b-129">Aşağıdaki örnek, genel bir aracın varsayılan konuma nasıl yükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8b56b-129">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="8b56b-130">Araç yüklenemezse hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-130">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="8b56b-131">Beklediğiniz akışların denetlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8b56b-131">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="8b56b-132">Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, sürüm numarasını aşağıdaki biçimi kullanarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b56b-132">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="8b56b-133">Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="8b56b-133">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="8b56b-134">Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-134">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="8b56b-135">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8b56b-135">The default directories are:</span></span>

| <span data-ttu-id="8b56b-136">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="8b56b-136">OS</span></span>          | <span data-ttu-id="8b56b-137">Yol</span><span class="sxs-lookup"><span data-stu-id="8b56b-137">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="8b56b-138">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="8b56b-138">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="8b56b-139">Windows</span><span class="sxs-lookup"><span data-stu-id="8b56b-139">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="8b56b-140">Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-140">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="8b56b-141">Genel araçların makineye genel değil, kullanıcıya özgü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b56b-141">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="8b56b-142">Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-142">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="8b56b-143">Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-143">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="8b56b-144">Genel araçlar, belirli bir dizine de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-144">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="8b56b-145">Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-145">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="8b56b-146">Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="8b56b-146">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="8b56b-147">Aracı kullanma</span><span class="sxs-lookup"><span data-stu-id="8b56b-147">Use the tool</span></span>

<span data-ttu-id="8b56b-148">Araç yüklendikten sonra, komutunu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b56b-148">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="8b56b-149">Komutun paket adı ile aynı olamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b56b-149">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="8b56b-150">Komut `dotnetsay`ise, şunu ile çağırın:</span><span class="sxs-lookup"><span data-stu-id="8b56b-150">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="8b56b-151">Araç yazarı aracın `dotnet` istem bağlamında görünmesini istiyorlarsa, bu, örneğin şöyle bir şekilde `dotnet <command>`çağrılabileceği şekilde yazmış olabilirler:</span><span class="sxs-lookup"><span data-stu-id="8b56b-151">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="8b56b-152">Yüklü paketleri [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak listeleyerek, yüklü bir genel araç paketine hangi araçların ekleneceğini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b56b-152">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="8b56b-153">Ayrıca, aracın Web sitesinde veya aşağıdaki komutlardan birini yazarak kullanım yönergelerine bakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b56b-153">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a><span data-ttu-id="8b56b-154">Diğer CLı komutları</span><span class="sxs-lookup"><span data-stu-id="8b56b-154">Other CLI commands</span></span>

<span data-ttu-id="8b56b-155">.NET Core SDK .NET Core küresel araçlarını destekleyen diğer komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-155">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="8b56b-156">Aşağıdaki seçeneklerden biriyle `dotnet tool` komutlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b56b-156">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="8b56b-157">`--global` veya `-g`, komutun Kullanıcı genelindeki genel araçlara uygun olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-157">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="8b56b-158">`--tool-path` genel araçlar için özel bir konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-158">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="8b56b-159">Genel araçlar için hangi komutların kullanılabildiğini öğrenmek için:</span><span class="sxs-lookup"><span data-stu-id="8b56b-159">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="8b56b-160">Küresel bir aracın güncelleştirilmesi, en son kararlı sürümle kaldırılması ve yeniden yüklenmesi ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="8b56b-160">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="8b56b-161">Genel bir aracı güncelleştirmek için [DotNet Aracı güncelleştirme](dotnet-tool-update.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b56b-161">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="8b56b-162">[DotNet aracını kaldırma](dotnet-tool-uninstall.md)Işlemini kullanarak genel bir aracı kaldırma:</span><span class="sxs-lookup"><span data-stu-id="8b56b-162">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="8b56b-163">Makinede yüklü olan tüm genel araçları, sürüm ve komutlarıyla birlikte göstermek için [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b56b-163">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a><span data-ttu-id="8b56b-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b56b-164">See also</span></span>

* [<span data-ttu-id="8b56b-165">.NET Core araç kullanımı sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="8b56b-165">Troubleshoot .NET Core tool usage issues</span></span>](troubleshoot-usage-issues.md)

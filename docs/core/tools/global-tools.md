---
title: .NET Core küresel araçları
description: .NET Core genel araçlarının ne olduğuna ve bunlara yönelik .NET Core CLI komutlarına genel bakış.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 40a0aabcf523e8dac9a3ad226064bbb3c1b3ce5b
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332016"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="acdc3-103">.NET Core genel araçlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="acdc3-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="acdc3-104">.NET Core küresel Aracı, konsol uygulaması içeren özel bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="acdc3-105">Bir genel araç, makinenizde, PATH ortam değişkenine veya özel bir konuma dahil olan varsayılan bir konumda yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="acdc3-106">.NET Core küresel aracı kullanmak istiyorsanız:</span><span class="sxs-lookup"><span data-stu-id="acdc3-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="acdc3-107">Araçla ilgili bilgileri bulun (genellikle bir Web sitesi veya GitHub sayfası).</span><span class="sxs-lookup"><span data-stu-id="acdc3-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="acdc3-108">Akışın giriş sayfasındaki yazar ve istatistikleri denetleyin (genellikle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="acdc3-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="acdc3-109">Aracı 'nı yükler.</span><span class="sxs-lookup"><span data-stu-id="acdc3-109">Install the tool.</span></span>
* <span data-ttu-id="acdc3-110">Aracı çağırın.</span><span class="sxs-lookup"><span data-stu-id="acdc3-110">Call the tool.</span></span>
* <span data-ttu-id="acdc3-111">Aracı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="acdc3-111">Update the tool.</span></span>
* <span data-ttu-id="acdc3-112">Aracı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="acdc3-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="acdc3-113">.NET Core küresel araçları yolunuzda görünür ve tam güvende çalışır.</span><span class="sxs-lookup"><span data-stu-id="acdc3-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="acdc3-114">Yazara güvenmediğiniz .NET Core küresel araçlarını yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="acdc3-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="acdc3-115">.NET Core küresel aracı bulma</span><span class="sxs-lookup"><span data-stu-id="acdc3-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="acdc3-116">Şu anda .NET Core komut satırı arabiriminde (CLı) genel bir araç arama özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="acdc3-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="acdc3-117">[NuGet](https://www.nuget.org)üzerinde .NET Core küresel araçları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acdc3-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="acdc3-118">Ancak, NuGet henüz .NET Core küresel araçları için arama yapmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="acdc3-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="acdc3-119">Ayrıca, blog gönderilerinde veya [natemcmaster/DotNet-Tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposunda araç önerileri de bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acdc3-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="acdc3-120">[ASPNET/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub deposunda ASP.NET ekibi tarafından oluşturulan genel araçların kaynak kodunu da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acdc3-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="acdc3-121">Yazarı ve istatistikleri denetleme</span><span class="sxs-lookup"><span data-stu-id="acdc3-121">Check the author and statistics</span></span>

<span data-ttu-id="acdc3-122">.NET Core küresel araçları tam güvende çalıştığı ve genellikle yolunuza yüklendiği için, bu, çok güçlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="acdc3-123">Güvenmediğiniz kişilerden araç indirmeyin.</span><span class="sxs-lookup"><span data-stu-id="acdc3-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="acdc3-124">Araç NuGet üzerinde barındırılıyorsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acdc3-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="acdc3-125">Küresel bir araç yükler</span><span class="sxs-lookup"><span data-stu-id="acdc3-125">Install a Global Tool</span></span>

<span data-ttu-id="acdc3-126">Küresel bir araç yüklemek için [DotNet aracı install](dotnet-tool-install.md) .NET Core CLI komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="acdc3-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="acdc3-127">Aşağıdaki örnek, genel bir aracın varsayılan konuma nasıl yükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="acdc3-127">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="acdc3-128">Araç yüklenemezse hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="acdc3-129">Beklediğiniz akışların denetlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="acdc3-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="acdc3-130">Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, sürüm numarasını aşağıdaki biçimi kullanarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="acdc3-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="acdc3-131">Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="acdc3-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="acdc3-132">Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="acdc3-133">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="acdc3-133">The default directories are:</span></span>

| <span data-ttu-id="acdc3-134">OS</span><span class="sxs-lookup"><span data-stu-id="acdc3-134">OS</span></span>          | <span data-ttu-id="acdc3-135">`Path`</span><span class="sxs-lookup"><span data-stu-id="acdc3-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="acdc3-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="acdc3-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="acdc3-137">Windows</span><span class="sxs-lookup"><span data-stu-id="acdc3-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="acdc3-138">Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="acdc3-139">Genel araçların makineye genel değil, kullanıcıya özgü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="acdc3-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="acdc3-140">Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="acdc3-141">Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="acdc3-142">Genel araçlar, belirli bir dizine de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="acdc3-143">Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="acdc3-144">Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="acdc3-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="acdc3-145">Aracı kullanma</span><span class="sxs-lookup"><span data-stu-id="acdc3-145">Use the tool</span></span>

<span data-ttu-id="acdc3-146">Araç yüklendikten sonra, komutunu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acdc3-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="acdc3-147">Komutun paket adı ile aynı olamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="acdc3-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="acdc3-148">Komut ise `dotnetsay`, şunu ile çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="acdc3-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="acdc3-149">Araç yazarı, aracın `dotnet` istem bağlamında görünmesini istiyorlarsa, bu, şöyle bir şekilde bir `dotnet <command>`şekilde yazmış olabilirler, örneğin:</span><span class="sxs-lookup"><span data-stu-id="acdc3-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="acdc3-150">Yüklü paketleri [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak listeleyerek, yüklü bir genel araç paketine hangi araçların ekleneceğini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acdc3-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="acdc3-151">Ayrıca, aracın Web sitesinde veya aşağıdaki komutlardan birini yazarak kullanım yönergelerine bakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="acdc3-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a><span data-ttu-id="acdc3-152">Diğer CLı komutları</span><span class="sxs-lookup"><span data-stu-id="acdc3-152">Other CLI commands</span></span>

<span data-ttu-id="acdc3-153">.NET Core SDK .NET Core küresel araçlarını destekleyen diğer komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-153">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="acdc3-154">Aşağıdaki seçeneklerden biriyle komutlardan birini kullanın: `dotnet tool`</span><span class="sxs-lookup"><span data-stu-id="acdc3-154">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="acdc3-155">`--global`ya `-g` da komutun Kullanıcı genelindeki genel araçlara uygun olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-155">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="acdc3-156">`--tool-path`Küresel araçlar için özel bir konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-156">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="acdc3-157">Genel araçlar için hangi komutların kullanılabildiğini öğrenmek için:</span><span class="sxs-lookup"><span data-stu-id="acdc3-157">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="acdc3-158">Küresel bir aracın güncelleştirilmesi, en son kararlı sürümle kaldırılması ve yeniden yüklenmesi ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="acdc3-158">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="acdc3-159">Genel bir aracı güncelleştirmek için [DotNet Aracı güncelleştirme](dotnet-tool-update.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="acdc3-159">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="acdc3-160">[DotNet aracını kaldırma](dotnet-tool-uninstall.md)Işlemini kullanarak genel bir aracı kaldırma:</span><span class="sxs-lookup"><span data-stu-id="acdc3-160">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="acdc3-161">Makinede yüklü olan tüm genel araçları, sürüm ve komutlarıyla birlikte göstermek için [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="acdc3-161">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a><span data-ttu-id="acdc3-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acdc3-162">See also</span></span>

* [<span data-ttu-id="acdc3-163">.NET Core araç kullanımı sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="acdc3-163">Troubleshoot .NET Core tool usage issues</span></span>](troubleshoot-usage-issues.md)

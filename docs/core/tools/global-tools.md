---
title: .NET araçları
description: .NET araçları 'nı yüklemek, kullanmak, güncelleştirmek ve kaldırmak. Küresel araçlar, araç yolu araçları ve yerel araçları içerir.
author: KathleenDollard
ms.topic: how-to
ms.date: 02/12/2020
ms.openlocfilehash: 8839fd4fba72c9f973d906eabb72919306a847dd
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633890"
---
# <a name="how-to-manage-net-tools"></a><span data-ttu-id="30c11-104">.NET araçlarını yönetme</span><span class="sxs-lookup"><span data-stu-id="30c11-104">How to manage .NET tools</span></span>

<span data-ttu-id="30c11-105">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="30c11-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="30c11-106">.NET aracı, konsol uygulaması içeren özel bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="30c11-106">A .NET tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="30c11-107">Aşağıdaki yollarla makinenize bir araç yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="30c11-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="30c11-108">Genel bir araç olarak.</span><span class="sxs-lookup"><span data-stu-id="30c11-108">As a global tool.</span></span>

  <span data-ttu-id="30c11-109">Araç ikilileri, PATH ortam değişkenine eklenen bir varsayılan dizine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="30c11-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="30c11-110">Aracı, konumunu belirtmeden makinedeki herhangi bir dizinden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c11-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="30c11-111">Makinedeki tüm dizinler için bir aracın bir sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30c11-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="30c11-112">Özel bir konumda (araç yolu aracı olarak da bilinir) genel bir araç olarak.</span><span class="sxs-lookup"><span data-stu-id="30c11-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="30c11-113">Araç ikilileri, belirttiğiniz bir konuma yüklenir.</span><span class="sxs-lookup"><span data-stu-id="30c11-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="30c11-114">Aracı, yükleme dizininden ya da komut adı ile dizin sağlayarak ya da yolu PATH ortam değişkenine ekleyerek çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c11-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="30c11-115">Makinedeki tüm dizinler için bir aracın bir sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30c11-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="30c11-116">Yerel bir araç olarak (.NET Core SDK 3,0 ve üzeri için geçerlidir).</span><span class="sxs-lookup"><span data-stu-id="30c11-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="30c11-117">Araç ikilileri bir varsayılan dizine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="30c11-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="30c11-118">Aracı, yükleme dizininden veya alt dizinlerinden herhangi birine çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c11-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="30c11-119">Farklı dizinler aynı aracın farklı sürümlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="30c11-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="30c11-120">.NET CLı, bir dizine yerel olarak hangi araçların yüklendiğini izlemek için bildirim dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="30c11-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="30c11-121">Bildirim dosyası bir kaynak kod deposunun kök dizininde kaydedildiğinde, katılımcı depoyu kopyalayabilir ve bildirim dosyalarında listelenen tüm araçları yükleyen tek bir .NET CLı komutu çağırabilirler.</span><span class="sxs-lookup"><span data-stu-id="30c11-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30c11-122">.NET araçları tam güvende çalışır.</span><span class="sxs-lookup"><span data-stu-id="30c11-122">.NET tools run in full trust.</span></span> <span data-ttu-id="30c11-123">Yazara güvenmediğiniz müddetçe .NET aracını yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="30c11-123">Do not install a .NET tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="30c11-124">Araç bulun</span><span class="sxs-lookup"><span data-stu-id="30c11-124">Find a tool</span></span>

<span data-ttu-id="30c11-125">Araç bulmak için bazı yollar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="30c11-125">Here are some ways to find tools:</span></span>

* <span data-ttu-id="30c11-126">NuGet.org 'e yayınlanan bir araç bulmak için [DotNet aracı arama](dotnet-tool-search.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="30c11-126">Use the [dotnet tool search](dotnet-tool-search.md) command to find a tool that is published to NuGet.org.</span></span>
* <span data-ttu-id="30c11-127">".NET aracı" paket türü filtresini kullanarak [NuGet](https://www.nuget.org) Web sitesinde arama yapın.</span><span class="sxs-lookup"><span data-stu-id="30c11-127">Search the [NuGet](https://www.nuget.org) website by using the ".NET tool" package type filter.</span></span> <span data-ttu-id="30c11-128">Daha fazla bilgi için bkz. [paketleri bulma ve seçme](/nuget/consume-packages/finding-and-choosing-packages).</span><span class="sxs-lookup"><span data-stu-id="30c11-128">For more information, see [Finding and choosing packages](/nuget/consume-packages/finding-and-choosing-packages).</span></span>
* <span data-ttu-id="30c11-129">[DotNet/aspnetcore GitHub deposunun Araçlar dizininde](https://github.com/dotnet/aspnetcore/tree/master/src/Tools)ASP.NET Core ekibi tarafından oluşturulan araçların kaynak koduna bakın.</span><span class="sxs-lookup"><span data-stu-id="30c11-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="30c11-130">[.Net tanılama araçları](../diagnostics/index.md#net-core-diagnostic-global-tools)'nda tanılama araçları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="30c11-130">Learn about diagnostic tools at [.NET diagnostic tools](../diagnostics/index.md#net-core-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="30c11-131">Yazarı ve istatistikleri denetleme</span><span class="sxs-lookup"><span data-stu-id="30c11-131">Check the author and statistics</span></span>

<span data-ttu-id="30c11-132">.NET araçları tam güvende çalıştırıldıklarından ve genel araçlar PATH ortam değişkenine eklendiğinden, bunlar çok güçlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="30c11-132">Since .NET tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="30c11-133">Güvenmediğiniz kişilerden araç indirmeyin.</span><span class="sxs-lookup"><span data-stu-id="30c11-133">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="30c11-134">Araç NuGet üzerinde barındırılıyorsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c11-134">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="30c11-135">Küresel bir araç yükler</span><span class="sxs-lookup"><span data-stu-id="30c11-135">Install a global tool</span></span>

<span data-ttu-id="30c11-136">Bir aracı genel araç olarak yüklemek için, `-g` `--global` Aşağıdaki örnekte gösterildiği gibi [DotNet aracının Install](dotnet-tool-install.md)veya seçeneğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="30c11-136">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="30c11-137">Çıktı, aşağıdaki örneğe benzer şekilde aracı ve yüklü sürümü çağırmak için kullanılan komutu gösterir:</span><span class="sxs-lookup"><span data-stu-id="30c11-137">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="30c11-138">Bir araç ikililerinin varsayılan konumu işletim sistemine bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="30c11-138">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="30c11-139">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="30c11-139">OS</span></span>          | <span data-ttu-id="30c11-140">Yol</span><span class="sxs-lookup"><span data-stu-id="30c11-140">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="30c11-141">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="30c11-141">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="30c11-142">Windows</span><span class="sxs-lookup"><span data-stu-id="30c11-142">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="30c11-143">SDK ilk çalıştırıldığında, bu konum kullanıcının yoluna eklenir, bu nedenle genel araçlar araç konumunu belirtmeden herhangi bir dizinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="30c11-143">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="30c11-144">Araç erişimi, makineye genel değil, kullanıcıya özeldir.</span><span class="sxs-lookup"><span data-stu-id="30c11-144">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="30c11-145">Genel araç yalnızca aracı yükleyen kullanıcı tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30c11-145">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="30c11-146">Özel bir konuma genel araç yükler</span><span class="sxs-lookup"><span data-stu-id="30c11-146">Install a global tool in a custom location</span></span>

<span data-ttu-id="30c11-147">Bir aracı özel bir konuma genel araç olarak yüklemek için, `--tool-path` Aşağıdaki örneklerde gösterildiği gibi [DotNet araç install](dotnet-tool-install.md)seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="30c11-147">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="30c11-148">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="30c11-148">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="30c11-149">Linux veya macOS 'ta:</span><span class="sxs-lookup"><span data-stu-id="30c11-149">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="30c11-150">.NET SDK bu konumu otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="30c11-150">The .NET SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="30c11-151">[Bir araç yolu aracını çağırmak](#invoke-a-tool-path-tool)için aşağıdaki yöntemlerden birini kullanarak komutun kullanılabilir olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="30c11-151">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="30c11-152">Yükleme dizinini PATH ortam değişkenine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="30c11-152">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="30c11-153">Aracı çağırdığınızda aracın tam yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="30c11-153">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="30c11-154">Yükleme dizini içinden aracı çağırın.</span><span class="sxs-lookup"><span data-stu-id="30c11-154">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="30c11-155">Yerel bir araç yükler</span><span class="sxs-lookup"><span data-stu-id="30c11-155">Install a local tool</span></span>

<span data-ttu-id="30c11-156">**.NET Core 3,0 SDK ve üzeri için geçerlidir.**</span><span class="sxs-lookup"><span data-stu-id="30c11-156">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="30c11-157">Yalnızca yerel erişim için bir araç yüklemek üzere (geçerli dizin ve alt dizinler için), aracın bir araç bildirim dosyasına eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="30c11-157">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="30c11-158">Bir araç bildirim dosyası oluşturmak için şu komutu çalıştırın `dotnet new tool-manifest` :</span><span class="sxs-lookup"><span data-stu-id="30c11-158">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="30c11-159">Bu komut, *. config* dizininde *dotnet-tools.js* adlı bir bildirim dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30c11-159">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="30c11-160">Bildirim dosyasına yerel bir araç eklemek için, [DotNet aracı install](dotnet-tool-install.md) komutunu kullanın ve  `--global` `--tool-path` Aşağıdaki örnekte gösterildiği gibi, ve seçeneklerini atlayın:</span><span class="sxs-lookup"><span data-stu-id="30c11-160">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="30c11-161">Komut çıktısı, aşağıdaki örneğe benzer şekilde, yeni yüklenen aracın hangi bildirim dosyasına olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="30c11-161">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="30c11-162">Aşağıdaki örnekte, iki yerel araç yüklü olan bir bildirim dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="30c11-162">The following example shows a manifest file with two local tools installed:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

<span data-ttu-id="30c11-163">Genellikle deponun kök dizinine yerel bir araç eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="30c11-163">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="30c11-164">Bildirim dosyasını depoya iade ettikten sonra, depodan kod kullanıma alan geliştiriciler en son bildirim dosyasını alır.</span><span class="sxs-lookup"><span data-stu-id="30c11-164">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="30c11-165">Bildirim dosyasında listelenen tüm araçları yüklemek için şu komutu çalıştırırlar `dotnet tool restore` :</span><span class="sxs-lookup"><span data-stu-id="30c11-165">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="30c11-166">Çıktı hangi araçların geri yüklendiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="30c11-166">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="30c11-167">Belirli bir araç sürümünü yükler</span><span class="sxs-lookup"><span data-stu-id="30c11-167">Install a specific tool version</span></span>

<span data-ttu-id="30c11-168">Bir aracın yayın öncesi sürümünü veya belirli bir sürümünü yüklemek için, `--version` Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak sürüm numarasını belirtin:</span><span class="sxs-lookup"><span data-stu-id="30c11-168">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="30c11-169">Araç kullanma</span><span class="sxs-lookup"><span data-stu-id="30c11-169">Use a tool</span></span>

<span data-ttu-id="30c11-170">Bir aracı çağırmak için kullandığınız komut, yüklediğiniz paketin adından farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="30c11-170">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="30c11-171">Geçerli Kullanıcı için makinede yüklü olan tüm araçları göstermek için [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="30c11-171">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="30c11-172">Çıktı, aşağıdaki örneğe benzer şekilde her bir aracın sürümünü ve komutunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="30c11-172">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="30c11-173">Bu örnekte gösterildiği gibi listede yerel araçlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="30c11-173">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="30c11-174">Genel araçları görmek için `--global` seçeneğini kullanın ve araç yolu araçlarını görmek için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="30c11-174">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="30c11-175">Küresel bir araç çağır</span><span class="sxs-lookup"><span data-stu-id="30c11-175">Invoke a global tool</span></span>

<span data-ttu-id="30c11-176">Genel araçlar için, araç komutunu kendi kendine kullanın.</span><span class="sxs-lookup"><span data-stu-id="30c11-176">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="30c11-177">Örneğin, komut `dotnetsay` veya ise `dotnet-doc` , bu, komutu çağırmak için kullandığınız şeydir:</span><span class="sxs-lookup"><span data-stu-id="30c11-177">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="30c11-178">Komut önekiyle başlıyorsa `dotnet-` , aracı çağırmak için alternatif bir yol, `dotnet` komutunu kullanmak ve araç komut önekini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="30c11-178">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="30c11-179">Örneğin, komut ise, `dotnet-doc` aşağıdaki komut aracı çağırır:</span><span class="sxs-lookup"><span data-stu-id="30c11-179">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="30c11-180">Ancak, aşağıdaki senaryoda `dotnet` küresel bir araç çağırmak için komutunu kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="30c11-180">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="30c11-181">Küresel bir araç ve yerel bir araç tarafından önekli aynı komut vardır `dotnet-` .</span><span class="sxs-lookup"><span data-stu-id="30c11-181">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="30c11-182">Genel aracı yerel araç kapsamında olan bir dizinden çağırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="30c11-182">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="30c11-183">Bu senaryoda `dotnet doc` ve `dotnet dotnet-doc` Yerel Aracı çağırın.</span><span class="sxs-lookup"><span data-stu-id="30c11-183">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="30c11-184">Genel aracı çağırmak için, komutu kendi başına kullanın:</span><span class="sxs-lookup"><span data-stu-id="30c11-184">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="30c11-185">Araç yolu aracı çağırma</span><span class="sxs-lookup"><span data-stu-id="30c11-185">Invoke a tool-path tool</span></span>

<span data-ttu-id="30c11-186">Seçeneği kullanılarak yüklenen küresel bir aracı çağırmak için `tool-path` , [Bu makalede daha önce](#install-a-global-tool-in-a-custom-location)anlatıldığı gibi komutun kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="30c11-186">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="30c11-187">Yerel bir araç çağır</span><span class="sxs-lookup"><span data-stu-id="30c11-187">Invoke a local tool</span></span>

<span data-ttu-id="30c11-188">Yerel bir aracı çağırmak için, `dotnet` yükleme dizini içinden komutunu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="30c11-188">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="30c11-189">`dotnet tool run <COMMAND_NAME>`Aşağıdaki örneklerde gösterildiği gibi Long formunu () veya kısa biçimi ( `dotnet <COMMAND_NAME>` ) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30c11-189">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="30c11-190">Komutun öneki varsa `dotnet-` , aracı çağırdığınızda öneki dahil edebilir veya atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c11-190">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="30c11-191">Örneğin, komut ise `dotnet-doc` Aşağıdaki örneklerden herhangi biri yerel aracı çağırır:</span><span class="sxs-lookup"><span data-stu-id="30c11-191">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="30c11-192">Bir aracı güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="30c11-192">Update a tool</span></span>

<span data-ttu-id="30c11-193">Bir aracın güncelleştirilmesi, en son kararlı sürümle birlikte kaldırılıp yeniden yüklenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="30c11-193">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="30c11-194">Bir aracı güncelleştirmek için, bu aracı yüklemek için kullandığınız seçenekle [DotNet araç Update](dotnet-tool-update.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="30c11-194">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="30c11-195">Yerel bir araç için SDK, geçerli dizin ve üst dizinlere bakarak paket KIMLIĞINI içeren ilk bildirim dosyasını bulur.</span><span class="sxs-lookup"><span data-stu-id="30c11-195">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="30c11-196">Herhangi bir bildirim dosyasında böyle bir paket KIMLIĞI yoksa, SDK en yakın bildirim dosyasına yeni bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="30c11-196">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="30c11-197">Araç kaldırma</span><span class="sxs-lookup"><span data-stu-id="30c11-197">Uninstall a tool</span></span>

<span data-ttu-id="30c11-198">Bir aracı, aracı yüklemek için kullandığınız seçenekle [DotNet Aracı kaldırma](dotnet-tool-uninstall.md) komutunu kullanarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="30c11-198">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="30c11-199">Yerel bir araç için SDK, geçerli dizin ve üst dizinlere bakarak paket KIMLIĞINI içeren ilk bildirim dosyasını bulur.</span><span class="sxs-lookup"><span data-stu-id="30c11-199">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="30c11-200">Yardım alın ve sorun giderin</span><span class="sxs-lookup"><span data-stu-id="30c11-200">Get help and troubleshoot</span></span>

<span data-ttu-id="30c11-201">Kullanılabilir komutların bir listesini almak için `dotnet tool` aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="30c11-201">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="30c11-202">Araç kullanım yönergelerini almak için aşağıdaki komutlardan birini girin veya aracın Web sitesini görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="30c11-202">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="30c11-203">Bir araç yüklenemediğinde veya çalışmazsa, bkz. [.NET araç kullanımı sorunlarını giderme](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="30c11-203">If a tool fails to install or run, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30c11-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30c11-204">See also</span></span>

- [<span data-ttu-id="30c11-205">Öğretici: .NET CLı kullanarak .NET aracı oluşturma</span><span class="sxs-lookup"><span data-stu-id="30c11-205">Tutorial: Create a .NET tool using the .NET CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="30c11-206">Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="30c11-206">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="30c11-207">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="30c11-207">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)

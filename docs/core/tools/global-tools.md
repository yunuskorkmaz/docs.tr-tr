---
title: .NET Çekirdek araçları
description: .NET Core araçlarının nasıl yüklenir, kullanılır, güncellenir ve kaldırılır. Genel araçları, araç yolu araçlarını ve yerel araçları kapsar.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847799"
---
# <a name="how-to-manage-net-core-tools"></a><span data-ttu-id="31b04-104">.NET Core araçları nasıl yönetilir?</span><span class="sxs-lookup"><span data-stu-id="31b04-104">How to manage .NET Core tools</span></span>

<span data-ttu-id="31b04-105">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="31b04-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="31b04-106">.NET Core aracı, konsol uygulaması içeren özel bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="31b04-106">A .NET Core tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="31b04-107">Bir alet makinenize aşağıdaki yollarla takılabilir:</span><span class="sxs-lookup"><span data-stu-id="31b04-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="31b04-108">Küresel bir araç olarak.</span><span class="sxs-lookup"><span data-stu-id="31b04-108">As a global tool.</span></span>

  <span data-ttu-id="31b04-109">Araç ikilileri, PATH ortamı değişkenine eklenen varsayılan bir dizine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="31b04-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="31b04-110">Aracı konumunu belirtmeden makinedeki herhangi bir dizinden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31b04-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="31b04-111">Bir aletin bir sürümü makinedeki tüm dizinler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31b04-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="31b04-112">Özel bir konumda genel bir araç olarak (araç yolu aracı olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="31b04-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="31b04-113">Araç ikilileri belirttiğiniz bir konuma yüklenir.</span><span class="sxs-lookup"><span data-stu-id="31b04-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="31b04-114">Aracı yükleme dizininden veya komut adı ile dizini sağlayarak veya dizini PATH ortamı değişkenine ekleyerek çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31b04-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="31b04-115">Bir aletin bir sürümü makinedeki tüm dizinler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31b04-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="31b04-116">Yerel bir araç olarak (.NET Core SDK 3.0 ve sonrası için geçerlidir).</span><span class="sxs-lookup"><span data-stu-id="31b04-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="31b04-117">Araç ikilileri varsayılan bir dizinde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="31b04-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="31b04-118">Aracı yükleme dizininden veya alt dizinişlerinden çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="31b04-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="31b04-119">Farklı dizinler aynı aracın farklı sürümlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="31b04-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="31b04-120">.NET CLI, hangi araçların bir dizine yerel olarak yüklenmiş olarak yüklendiğine göre bildirim dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="31b04-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="31b04-121">Bildirim dosyası bir kaynak kodu deposunun kök dizinine kaydedildiğinde, katılımcı depoyu klonlayabilir ve bildirim dosyalarında listelenen tüm araçları yükleyen tek bir .NET Core CLI komutunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="31b04-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET Core CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31b04-122">.NET Core araçları tam güven içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="31b04-122">.NET Core tools run in full trust.</span></span> <span data-ttu-id="31b04-123">Yazara güvenmediğiniz sürece bir .NET Core aracı yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="31b04-123">Do not install a .NET Core tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="31b04-124">Bir araç bulma</span><span class="sxs-lookup"><span data-stu-id="31b04-124">Find a tool</span></span>

<span data-ttu-id="31b04-125">Şu anda,.NET Core'un bir araç arama özelliği yok.</span><span class="sxs-lookup"><span data-stu-id="31b04-125">Currently, .NET Core doesn't have a tool search feature.</span></span> <span data-ttu-id="31b04-126">Araçları bulmanın bazı yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="31b04-126">Here are some ways to find tools:</span></span>

* <span data-ttu-id="31b04-127">[Natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposundaki araçların listesine bakın.</span><span class="sxs-lookup"><span data-stu-id="31b04-127">See the list of tools in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="31b04-128">.NET araçlarını aramak için [ToolGet'i](https://www.toolget.net/) kullanın.</span><span class="sxs-lookup"><span data-stu-id="31b04-128">Use [ToolGet](https://www.toolget.net/) to search for .NET tools.</span></span>
* <span data-ttu-id="31b04-129">ASP.NET Core ekibi tarafından oluşturulan araçların kaynak koduna [dotnet/aspnetcore GitHub deposunun Araçlar dizininde](https://github.com/dotnet/aspnetcore/tree/master/src/Tools)bakın.</span><span class="sxs-lookup"><span data-stu-id="31b04-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="31b04-130">[.NET Core dotnet tanılama araçları](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="31b04-130">Learn about diagnostic tools at [.NET Core dotnet diagnostic tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>
* <span data-ttu-id="31b04-131">[NuGet](https://www.nuget.org) web sitesini arayın.</span><span class="sxs-lookup"><span data-stu-id="31b04-131">Search the [NuGet](https://www.nuget.org) website.</span></span> <span data-ttu-id="31b04-132">Ancak, NuGet sitesinde henüz yalnızca araç paketleri için arama yapmanızı sağlayan bir özellik yoktur.</span><span class="sxs-lookup"><span data-stu-id="31b04-132">However, the NuGet site doesn't yet have a feature that lets you search only for tool packages.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="31b04-133">Yazarı ve istatistikleri kontrol edin</span><span class="sxs-lookup"><span data-stu-id="31b04-133">Check the author and statistics</span></span>

<span data-ttu-id="31b04-134">.NET Core araçları tam güven içinde çalıştırıladığından ve genel araçlar PATH ortamı değişkenine eklenmiştir, bunlar çok güçlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="31b04-134">Since .NET Core tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="31b04-135">Güvenmediğiniz kişilerden araçlar indirmeyin.</span><span class="sxs-lookup"><span data-stu-id="31b04-135">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="31b04-136">Araç NuGet'de barındırılırsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31b04-136">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="31b04-137">Genel bir araç yükleme</span><span class="sxs-lookup"><span data-stu-id="31b04-137">Install a global tool</span></span>

<span data-ttu-id="31b04-138">Bir aracı genel bir araç olarak `-g` `--global` yüklemek için, aşağıdaki örnekte gösterildiği [gibi, dotnet aracı yükleme](dotnet-tool-install.md)seçeneğini veya seçeneğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="31b04-138">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="31b04-139">Çıktı, aracı çağırmak için kullanılan komutu ve yüklenen sürümü aşağıdaki örneğe benzer şekilde gösterir:</span><span class="sxs-lookup"><span data-stu-id="31b04-139">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="31b04-140">Bir aracın ikilileri için varsayılan konum işletim sistemine bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="31b04-140">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="31b04-141">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="31b04-141">OS</span></span>          | <span data-ttu-id="31b04-142">Yol</span><span class="sxs-lookup"><span data-stu-id="31b04-142">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="31b04-143">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="31b04-143">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="31b04-144">Windows</span><span class="sxs-lookup"><span data-stu-id="31b04-144">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="31b04-145">Bu konum, SDK ilk çalıştırıldığında kullanıcının yoluna eklenir, böylece araç konumu belirtilmeden herhangi bir dizinden genel araçlar çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="31b04-145">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="31b04-146">Araç erişimi kullanıcıya özgüdür, makine geneli değildir.</span><span class="sxs-lookup"><span data-stu-id="31b04-146">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="31b04-147">Genel bir araç yalnızca aracı yükleyen kullanıcı tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31b04-147">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="31b04-148">Genel bir aracı özel bir konuma yükleme</span><span class="sxs-lookup"><span data-stu-id="31b04-148">Install a global tool in a custom location</span></span>

<span data-ttu-id="31b04-149">Bir aracı özel bir konumda genel bir araç `--tool-path` olarak yüklemek için, aşağıdaki örneklerde gösterildiği gibi [dotnet aracı yükleme](dotnet-tool-install.md)seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="31b04-149">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="31b04-150">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="31b04-150">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="31b04-151">Linux veya macOS'ta:</span><span class="sxs-lookup"><span data-stu-id="31b04-151">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="31b04-152">.NET Core SDK bu konumu PATH ortamı değişkenine otomatik olarak eklemez.</span><span class="sxs-lookup"><span data-stu-id="31b04-152">The .NET Core SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="31b04-153">[Bir araç yolu aracını çağırmak](#invoke-a-tool-path-tool)için, aşağıdaki yöntemlerden birini kullanarak komutun kullanılabilir olduğundan emin olsanız:</span><span class="sxs-lookup"><span data-stu-id="31b04-153">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="31b04-154">Yükleme dizini PATH ortamı değişkenine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31b04-154">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="31b04-155">Aracı çağırdığınızda araca giden tam yolu belirtin.</span><span class="sxs-lookup"><span data-stu-id="31b04-155">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="31b04-156">Aracı yükleme dizininin içinden çağırın.</span><span class="sxs-lookup"><span data-stu-id="31b04-156">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="31b04-157">Yerel bir araç yükleme</span><span class="sxs-lookup"><span data-stu-id="31b04-157">Install a local tool</span></span>

<span data-ttu-id="31b04-158">**.NET Core 3.0 SDK ve sonrası için geçerlidir.**</span><span class="sxs-lookup"><span data-stu-id="31b04-158">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="31b04-159">Yalnızca yerel erişim için bir araç yüklemek için (geçerli dizin ve alt dizinler için), bir araç bildirimi dosyasına eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="31b04-159">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="31b04-160">Bir araç bildirimi dosyası oluşturmak `dotnet new tool-manifest` için komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="31b04-160">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="31b04-161">Bu *komut,.config* dizininin altında *dotnet-tools.json* adlı bir bildirim dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31b04-161">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="31b04-162">Bildirim dosyasına yerel bir araç eklemek [için, dotnet aracı yükleme](dotnet-tool-install.md) komutunu kullanın ve aşağıdaki örnekte gösterildiği gibi `--global` seçenekleri `--tool-path` **atlayın:**</span><span class="sxs-lookup"><span data-stu-id="31b04-162">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="31b04-163">Komut çıktısı, yeni yüklenen aracın hangi dosyada olduğunu aşağıdaki örneğe benzer şekilde gösterir:</span><span class="sxs-lookup"><span data-stu-id="31b04-163">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="31b04-164">Aşağıdaki örnekte, iki yerel araç yüklü bir bildirim dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="31b04-164">The following example shows a manifest file with two local tools installed:</span></span>

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

<span data-ttu-id="31b04-165">Genellikle deponun kök dizinine yerel bir araç eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="31b04-165">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="31b04-166">Manifesto dosyasını depoya iade ettikten sonra, depodan kodu kullanıma alan geliştiriciler en son bildirim dosyasını alır.</span><span class="sxs-lookup"><span data-stu-id="31b04-166">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="31b04-167">Bildirim dosyasında listelenen tüm araçları yüklemek için `dotnet tool restore` aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="31b04-167">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="31b04-168">Çıktı, hangi araçların geri yüklendiğine işaret ediyor:</span><span class="sxs-lookup"><span data-stu-id="31b04-168">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="31b04-169">Belirli bir araç sürümünü yükleme</span><span class="sxs-lookup"><span data-stu-id="31b04-169">Install a specific tool version</span></span>

<span data-ttu-id="31b04-170">Bir ön sürüm sürümünü veya bir aracın belirli bir sürümünü yüklemek `--version` için, aşağıdaki örnekte gösterildiği gibi seçeneği kullanarak sürüm numarasını belirtin:</span><span class="sxs-lookup"><span data-stu-id="31b04-170">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="31b04-171">Bir araç kullanma</span><span class="sxs-lookup"><span data-stu-id="31b04-171">Use a tool</span></span>

<span data-ttu-id="31b04-172">Bir aracı çağırmak için kullandığınız komut, yüklediğiniz paketin adından farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="31b04-172">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="31b04-173">Geçerli kullanıcı için makinede yüklü olan tüm araçları görüntülemek için [dotnet araç listesi](dotnet-tool-list.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="31b04-173">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="31b04-174">Çıktı, aşağıdaki örneğe benzer şekilde her aracın sürümünü ve komutunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="31b04-174">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="31b04-175">Bu örnekte gösterildiği gibi, liste yerel araçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="31b04-175">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="31b04-176">Genel araçları görmek `--global` için, seçeneği kullanın ve araç yolu `--tool-path` araçlarını görmek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="31b04-176">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="31b04-177">Genel bir araç çağırma</span><span class="sxs-lookup"><span data-stu-id="31b04-177">Invoke a global tool</span></span>

<span data-ttu-id="31b04-178">Genel araçlar için araç komutunu tek başına kullanın.</span><span class="sxs-lookup"><span data-stu-id="31b04-178">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="31b04-179">Örneğin, komut, komutu çağırmak için kullandığınız `dotnetsay` komutise: `dotnet-doc`</span><span class="sxs-lookup"><span data-stu-id="31b04-179">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="31b04-180">Komut öneki `dotnet-`ile başlarsa, aracı çağırmanın alternatif bir yolu `dotnet` komutu kullanmak ve araç komutu önekini atlamaktır.</span><span class="sxs-lookup"><span data-stu-id="31b04-180">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="31b04-181">Örneğin, komut, `dotnet-doc`aşağıdaki komut aracı çağırır:</span><span class="sxs-lookup"><span data-stu-id="31b04-181">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="31b04-182">Ancak, aşağıdaki senaryoda genel bir `dotnet` araç çağırmak için komutu kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="31b04-182">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="31b04-183">Genel bir araç ve yerel bir araç `dotnet-`tarafından önceden belirlenmiş aynı komuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="31b04-183">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="31b04-184">Genel aracı yerel araç için kapsamda olan bir dizinden çağırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="31b04-184">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="31b04-185">Bu `dotnet doc` senaryoda, `dotnet dotnet-doc` ve yerel aracı çağırın.</span><span class="sxs-lookup"><span data-stu-id="31b04-185">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="31b04-186">Genel aracı çağırmak için komutu tek başına kullanın:</span><span class="sxs-lookup"><span data-stu-id="31b04-186">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="31b04-187">Araç yolu aracını çağırma</span><span class="sxs-lookup"><span data-stu-id="31b04-187">Invoke a tool-path tool</span></span>

<span data-ttu-id="31b04-188">Seçeneği kullanarak yüklenen genel bir aracı çağırmak için, bu makalede daha [önce](#install-a-global-tool-in-a-custom-location)açıklandığı gibi komutun kullanılabilir olduğundan emin olun. `tool-path`</span><span class="sxs-lookup"><span data-stu-id="31b04-188">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="31b04-189">Yerel bir aracı çağırma</span><span class="sxs-lookup"><span data-stu-id="31b04-189">Invoke a local tool</span></span>

<span data-ttu-id="31b04-190">Yerel bir aracı çağırmak için yükleme `dotnet` dizininin içinden komutu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31b04-190">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="31b04-191">Aşağıdaki örneklerde gösterildiği`dotnet tool run <COMMAND_NAME>`gibi uzun formu`dotnet <COMMAND_NAME>`( ) veya kısa formu ( ) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31b04-191">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="31b04-192">Komut önceden `dotnet-`belirlenmişse, aracı çağırırken önek'i ekleyebilir veya atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31b04-192">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="31b04-193">Örneğin, komut `dotnet-doc`, aşağıdaki örneklerden herhangi biri yerel aracı çağırır:</span><span class="sxs-lookup"><span data-stu-id="31b04-193">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="31b04-194">Aracı güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="31b04-194">Update a tool</span></span>

<span data-ttu-id="31b04-195">Bir aracı güncelleştirmek, bir aracı en son kararlı sürümle kaldırmayı ve yeniden yüklemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="31b04-195">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="31b04-196">Bir aracı güncelleştirmek için, aracı yüklemek için kullandığınız seçenekle [dotnet araç güncelleştirme](dotnet-tool-update.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="31b04-196">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="31b04-197">Yerel bir araç için SDK, geçerli dizin ve üst dizinlere bakarak paket kimliğini içeren ilk bildirim dosyasını bulur.</span><span class="sxs-lookup"><span data-stu-id="31b04-197">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="31b04-198">Herhangi bir bildirim dosyasında böyle bir paket kimliği yoksa, SDK en yakın bildirim dosyasına yeni bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="31b04-198">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="31b04-199">Aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="31b04-199">Uninstall a tool</span></span>

<span data-ttu-id="31b04-200">Aracı yüklemek için kullandığınız aynı seçenekle [dotnet aracı nı kaldır](dotnet-tool-uninstall.md) komutunu kullanarak bir aracı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="31b04-200">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="31b04-201">Yerel bir araç için SDK, geçerli dizin ve üst dizinlere bakarak paket kimliğini içeren ilk bildirim dosyasını bulur.</span><span class="sxs-lookup"><span data-stu-id="31b04-201">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="31b04-202">Yardım alın ve sorun giderme</span><span class="sxs-lookup"><span data-stu-id="31b04-202">Get help and troubleshoot</span></span>

<span data-ttu-id="31b04-203">Kullanılabilir `dotnet tool` komutların listesini almak için aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="31b04-203">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="31b04-204">Araç kullanım yönergelerini almak için aşağıdaki komutlardan birini girin veya aracın web sitesine bakın:</span><span class="sxs-lookup"><span data-stu-id="31b04-204">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="31b04-205">Bir araç yüklenmezse veya çalıştıramazsa, [Sorun Giderme .NET Core araç kullanım sorunları](troubleshoot-usage-issues.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="31b04-205">If a tool fails to install or run, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31b04-206">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31b04-206">See also</span></span>

- [<span data-ttu-id="31b04-207">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core aracı oluşturun</span><span class="sxs-lookup"><span data-stu-id="31b04-207">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="31b04-208">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="31b04-208">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="31b04-209">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="31b04-209">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)

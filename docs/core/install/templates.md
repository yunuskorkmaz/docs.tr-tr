---
title: SDK şablonlarını yükleyip yönetme-.NET Core
description: .NET Core şablonlarının Windows, Linux ve macOS 'a nasıl yükleneceğini öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 09acae1409eb0492be10bd3a61b14da5be57c6c7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324487"
---
# <a name="manage-net-project-and-item-templates"></a><span data-ttu-id="07ce7-103">.NET projesi ve öğe şablonlarını yönetme</span><span class="sxs-lookup"><span data-stu-id="07ce7-103">Manage .NET project and item templates</span></span>

<span data-ttu-id="07ce7-104">.NET Core, kullanıcıların NuGet, NuGet paket dosyası veya dosya sistemi dizininden şablon yüklemesine veya kaldırmasına olanak tanıyan bir şablon sistemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="07ce7-104">.NET Core provides a template system that enables users to install or uninstall templates from NuGet, a NuGet package file, or a file system directory.</span></span> <span data-ttu-id="07ce7-105">Bu makalede, .NET Core şablonlarının .NET Core SDK CLı aracılığıyla nasıl yönetileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="07ce7-105">This article describes how to manage .NET Core templates through the .NET Core SDK CLI.</span></span>

<span data-ttu-id="07ce7-106">Şablon oluşturma hakkında daha fazla bilgi için bkz. [öğretici: şablon oluşturma](../tutorials/cli-templates-create-item-template.md).</span><span class="sxs-lookup"><span data-stu-id="07ce7-106">For more information about creating templates, see [Tutorial: Create templates](../tutorials/cli-templates-create-item-template.md).</span></span>

## <a name="install-template"></a><span data-ttu-id="07ce7-107">Şablonu yükler</span><span class="sxs-lookup"><span data-stu-id="07ce7-107">Install template</span></span>

<span data-ttu-id="07ce7-108">Şablonlar [dotnet new](../tools/dotnet-new.md) , parametresiyle SDK komutu aracılığıyla yüklenir `-i` .</span><span class="sxs-lookup"><span data-stu-id="07ce7-108">Templates are installed through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-i` parameter.</span></span> <span data-ttu-id="07ce7-109">Bir şablonun NuGet paket tanımlayıcısını ya da şablon dosyalarını içeren bir klasörü sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ce7-109">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-hosted-package"></a><span data-ttu-id="07ce7-110">NuGet barındırılan paketi</span><span class="sxs-lookup"><span data-stu-id="07ce7-110">NuGet hosted package</span></span>

<span data-ttu-id="07ce7-111">.NET CLı şablonları, geniş dağıtım için [NuGet](https://www.nuget.org/) 'e yüklenir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-111">.NET CLI templates are uploaded to [NuGet](https://www.nuget.org/) for wide distribution.</span></span> <span data-ttu-id="07ce7-112">Şablonlar, özel bir akıştan da yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-112">Templates can also be installed from a private feed.</span></span> <span data-ttu-id="07ce7-113">Bir şablonu bir NuGet akışına yüklemek yerine, [Yerel NuGet paketi](#local-nuget-package) bölümünde açıklandığı gibi *nupkg* şablon dosyaları dağıtılabilir ve el ile yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-113">Instead of uploading a template to a NuGet feed, *nupkg* template files can be distributed and manually installed, as described in the [Local NuGet package](#local-nuget-package) section.</span></span>

<span data-ttu-id="07ce7-114">NuGet akışlarını yapılandırma hakkında daha fazla bilgi için bkz [dotnet nuget add source](../tools/dotnet-nuget-add-source.md) ..</span><span class="sxs-lookup"><span data-stu-id="07ce7-114">For more information about configuring NuGet feeds, see [dotnet nuget add source](../tools/dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="07ce7-115">Varsayılan NuGet akışından bir şablon paketi yüklemek için şu `dotnet new -i {package-id}` komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="07ce7-115">To install a template pack from the default NuGet feed, use the `dotnet new -i {package-id}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

<span data-ttu-id="07ce7-116">Varsayılan NuGet akışından belirli bir sürüme sahip bir şablon paketi yüklemek için şu `dotnet new -i {package-id}::{version}` komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="07ce7-116">To install a template pack from the default NuGet feed with a specific version, use the `dotnet new -i {package-id}::{version}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a><span data-ttu-id="07ce7-117">Yerel NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="07ce7-117">Local NuGet package</span></span>

<span data-ttu-id="07ce7-118">Bir şablon paketi oluşturulduğunda, bir *nupkg* dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="07ce7-118">When a template pack is created, a *nupkg* file is generated.</span></span> <span data-ttu-id="07ce7-119">Şablonlar içeren bir *nupkg* dosyanız varsa, şu `dotnet new -i {path-to-package}` komutla yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="07ce7-119">If you have a *nupkg* file containing templates, you can install it with the `dotnet new -i {path-to-package}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a><span data-ttu-id="07ce7-120">Klasör</span><span class="sxs-lookup"><span data-stu-id="07ce7-120">Folder</span></span>

<span data-ttu-id="07ce7-121">Bir *nupkg* dosyasından şablon yüklemeye alternatif olarak, bir klasörden şablonları doğrudan komutuyla da yükleyebilirsiniz `dotnet new -i {folder-path}` .</span><span class="sxs-lookup"><span data-stu-id="07ce7-121">As an alternative to installing template from a *nupkg* file, you can also install templates from a folder directly with the `dotnet new -i {folder-path}` command.</span></span> <span data-ttu-id="07ce7-122">Belirtilen klasör, bulunan herhangi bir şablon için şablon paketi tanımlayıcısı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-122">The folder specified is treated as the template pack identifier for any template found.</span></span> <span data-ttu-id="07ce7-123">Belirtilen klasör hiyerarşisinde bulunan tüm şablon yüklendi.</span><span class="sxs-lookup"><span data-stu-id="07ce7-123">Any template found in the specified folder's hierarchy is installed.</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

<span data-ttu-id="07ce7-124">`{folder-path}`Komutta belirtilen, bulunan tüm şablonlar için şablon paketi tanımlayıcısı olur.</span><span class="sxs-lookup"><span data-stu-id="07ce7-124">The `{folder-path}` specified on the command becomes the template pack identifier for all templates found.</span></span> <span data-ttu-id="07ce7-125">[Liste şablonları](#list-templates) bölümünde belirtildiği gibi, komutuyla yüklenmiş şablonların bir listesini alabilirsiniz `dotnet new -u` .</span><span class="sxs-lookup"><span data-stu-id="07ce7-125">As specified in the [List templates](#list-templates) section, you can get a list of templates installed with the `dotnet new -u` command.</span></span> <span data-ttu-id="07ce7-126">Bu örnekte, şablon paketi tanımlayıcısı, yüklemesi için kullanılan klasör olarak gösterilir:</span><span class="sxs-lookup"><span data-stu-id="07ce7-126">In this example, the template pack identifier is shown as the folder used for install:</span></span>

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a><span data-ttu-id="07ce7-127">Şablonu kaldır</span><span class="sxs-lookup"><span data-stu-id="07ce7-127">Uninstall template</span></span>

<span data-ttu-id="07ce7-128">Şablonlar, [dotnet new](../tools/dotnet-new.md) parametresiyle SDK komutu aracılığıyla kaldırılır `-u` .</span><span class="sxs-lookup"><span data-stu-id="07ce7-128">Templates are uninstalled through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-u` parameter.</span></span> <span data-ttu-id="07ce7-129">Bir şablonun NuGet paket tanımlayıcısını ya da şablon dosyalarını içeren bir klasörü sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ce7-129">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-package"></a><span data-ttu-id="07ce7-130">NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="07ce7-130">NuGet package</span></span>

<span data-ttu-id="07ce7-131">NuGet şablon paketi yüklendikten sonra, bir NuGet akışından veya *nupkg* dosyasından, NuGet paket tanımlayıcısına başvurarak uygulamayı kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ce7-131">After a NuGet template pack is installed, either from a NuGet feed or a *nupkg* file, you can uninstall it by referencing the NuGet package identifier.</span></span>

<span data-ttu-id="07ce7-132">Bir şablon paketini kaldırmak için şu komutu kullanın `dotnet new -u {package-id}` :</span><span class="sxs-lookup"><span data-stu-id="07ce7-132">To uninstall a template pack, use the `dotnet new -u {package-id}` command:</span></span>

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a><span data-ttu-id="07ce7-133">Klasör</span><span class="sxs-lookup"><span data-stu-id="07ce7-133">Folder</span></span>

<span data-ttu-id="07ce7-134">Şablonlar bir [klasör yolu](#folder)aracılığıyla yüklendiğinde, klasör yolu şablon paketi tanımlayıcısı olur.</span><span class="sxs-lookup"><span data-stu-id="07ce7-134">When templates are installed through a [folder path](#folder), the folder path becomes the template pack identifier.</span></span>

<span data-ttu-id="07ce7-135">Bir şablon paketini kaldırmak için şu komutu kullanın `dotnet new -u {package-folder-path}` :</span><span class="sxs-lookup"><span data-stu-id="07ce7-135">To uninstall a template pack, use the `dotnet new -u {package-folder-path}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a><span data-ttu-id="07ce7-136">Liste şablonları</span><span class="sxs-lookup"><span data-stu-id="07ce7-136">List templates</span></span>

<span data-ttu-id="07ce7-137">Standart kaldırma komutunu bir paket tanımlayıcısı olmadan kullanarak, yüklü şablonların bir listesini, her şablonu kaldırmak için olan komutla birlikte görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ce7-137">By using the standard uninstall command without a package identifier, you can see a list of installed templates along with the command that uninstalls each template.</span></span>

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a><span data-ttu-id="07ce7-138">Diğer SDK 'lardan şablon yükler</span><span class="sxs-lookup"><span data-stu-id="07ce7-138">Install templates from other SDKs</span></span>

<span data-ttu-id="07ce7-139">SDK 'nın her bir sürümünü sırayla yüklediyseniz, örneğin SDK 2,0 ' i ve SDK 2,1 ' yi yüklediyseniz ve bu nedenle, SDK 'nın şablonlarının her birini yüklemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="07ce7-139">If you've installed each version of the SDK sequentially, for example you installed SDK 2.0, then SDK 2.1, and so on, you'll have every SDK's templates installed.</span></span> <span data-ttu-id="07ce7-140">Bununla birlikte, 3,1 gibi daha sonraki bir SDK sürümüyle başlatırsanız, SDK 3,1 sürümü SDK 2,1 ve SDK 3,1 olduğunda yalnızca [LTS (uzun süreli destek) yayınları](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) için şablonlar dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-140">However, if you start with a later SDK version, like 3.1, only the templates for [LTS (long term support) releases](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) are included, which at the time of the SDK 3.1 release is SDK 2.1 and SDK 3.1.</span></span> <span data-ttu-id="07ce7-141">Başka bir sürüm için şablonlar dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-141">Templates for any other release aren't included.</span></span>

<span data-ttu-id="07ce7-142">.NET Core şablonları NuGet üzerinde bulunur ve bunları diğer tüm şablonlar gibi yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ce7-142">The .NET Core templates are available on NuGet, and you can install them like any other template.</span></span> <span data-ttu-id="07ce7-143">Daha fazla bilgi için bkz. [NuGet barındırılan paketini yükler](#nuget-hosted-package).</span><span class="sxs-lookup"><span data-stu-id="07ce7-143">For more information, see [Install NuGet hosted package](#nuget-hosted-package).</span></span>

| <span data-ttu-id="07ce7-144">SDK</span><span class="sxs-lookup"><span data-stu-id="07ce7-144">SDK</span></span>              | <span data-ttu-id="07ce7-145">NuGet paket tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="07ce7-145">NuGet Package Identifier</span></span>                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="07ce7-146">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="07ce7-146">.NET Core 2.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| <span data-ttu-id="07ce7-147">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="07ce7-147">.NET Core 2.2</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| <span data-ttu-id="07ce7-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="07ce7-148">.NET Core 3.0</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| <span data-ttu-id="07ce7-149">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="07ce7-149">.NET Core 3.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| <span data-ttu-id="07ce7-150">ASP.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="07ce7-150">ASP.NET Core 2.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| <span data-ttu-id="07ce7-151">ASP.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="07ce7-151">ASP.NET Core 2.2</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| <span data-ttu-id="07ce7-152">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="07ce7-152">ASP.NET Core 3.0</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| <span data-ttu-id="07ce7-153">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="07ce7-153">ASP.NET Core 3.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

<span data-ttu-id="07ce7-154">Örneğin .NET Core SDK, .NET Core 2,1 ve .NET Core 3,1 ' i hedefleyen bir konsol uygulaması için şablonlar içerir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-154">For example, the .NET Core SDK includes templates for a console app targeting .NET Core 2.1 and .NET Core 3.1.</span></span> <span data-ttu-id="07ce7-155">.NET Core 3,0 ' i hedeflemek istediyseniz, 3,0 şablonlarını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-155">If you wanted to target .NET Core 3.0, you would need to install the 3.0 templates.</span></span>

01. <span data-ttu-id="07ce7-156">.NET Core 3,0 ' i hedefleyen bir uygulama oluşturmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="07ce7-156">Try creating an app that targets .NET Core 3.0.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="07ce7-157">Bir hata iletisi görürseniz, şablonları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-157">If you see an error message, you need to install the templates.</span></span>

    > <span data-ttu-id="07ce7-158">Giriş ile eşleşen yüklü bir şablon bulunamadı, bu, çevrimiçi olarak aranıyor...</span><span class="sxs-lookup"><span data-stu-id="07ce7-158">Couldn't find an installed template that matches the input, searching online for one that does...</span></span>

01. <span data-ttu-id="07ce7-159">.NET Core 3,0 proje şablonlarını yükler.</span><span class="sxs-lookup"><span data-stu-id="07ce7-159">Install the .NET Core 3.0 project templates.</span></span>

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. <span data-ttu-id="07ce7-160">Uygulamayı ikinci kez oluşturmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="07ce7-160">Try creating the app a second time.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="07ce7-161">Projenin oluşturulduğunu belirten bir ileti görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ce7-161">And you should see a message indicating the project was created.</span></span>

    > <span data-ttu-id="07ce7-162">"Konsol uygulaması" şablonu başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="07ce7-162">The template "Console Application" was created successfully.</span></span>
    >
    > <span data-ttu-id="07ce7-163">Oluşturma sonrası eylemler işleniyor... Path-to-Project-File. csproj üzerinde ' dotnet restore ' çalıştırılıyor... Geri yüklenecek projeler belirleniyor... Path-to-Project-File. csproj için 1,05 sn 'de geri yükleme tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="07ce7-163">Processing post-creation actions... Running 'dotnet restore' on path-to-project-file.csproj... Determining projects to restore... Restore completed in 1.05 sec for path-to-project-file.csproj.</span></span>
    >
    > <span data-ttu-id="07ce7-164">Geri yükleme başarılı.</span><span class="sxs-lookup"><span data-stu-id="07ce7-164">Restore succeeded.</span></span>

## <a name="see-also"></a><span data-ttu-id="07ce7-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07ce7-165">See also</span></span>

- [<span data-ttu-id="07ce7-166">Öğretici: öğe şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="07ce7-166">Tutorial: Create an item template</span></span>](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)

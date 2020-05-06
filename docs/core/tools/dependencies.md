---
title: .NET Core 'da bağımlılıkları yönetme
description: Bir .NET Core uygulaması için proje bağımlılıklarının nasıl yönetileceğini açıklar.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 3e1d807ea69e66e31b277a92cd6a1dc0e76531b5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795553"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="5df66-103">.NET Core uygulamalarında bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="5df66-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="5df66-104">Bu makalede, proje dosyasını düzenleyerek veya CLı kullanarak bağımlılık ekleme ve kaldırma işlemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5df66-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="5df66-105">\<Packagereference> öğesi</span><span class="sxs-lookup"><span data-stu-id="5df66-105">The \<PackageReference> element</span></span>

<span data-ttu-id="5df66-106">`<PackageReference>` Proje dosyası öğesi aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5df66-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="5df66-107">`Include` Öznitelik, projeye eklenecek paketin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5df66-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="5df66-108">`Version` Öznitelik alınacak sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5df66-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="5df66-109">Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5df66-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="5df66-110">Proje dosyası söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5df66-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="5df66-111">Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:</span><span class="sxs-lookup"><span data-stu-id="5df66-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="5df66-112">Önceki örnekteki bağımlılık yalnızca derleme söz konusu hedef için varsa geçerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5df66-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="5df66-113">Koşulunda `$(TargetFramework)` , projede ayarlanmış bir MSBuild özelliği bulunur.</span><span class="sxs-lookup"><span data-stu-id="5df66-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="5df66-114">En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5df66-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="5df66-115">Proje dosyasını düzenleyerek bir bağımlılık ekleyin</span><span class="sxs-lookup"><span data-stu-id="5df66-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="5df66-116">Bir bağımlılık eklemek için bir `<PackageReference>` `<ItemGroup>` öğe içine bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5df66-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="5df66-117">Var olan `<ItemGroup>` bir veya yeni bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5df66-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="5df66-118">Aşağıdaki örnek, tarafından `dotnet new console`oluşturulan varsayılan konsol uygulaması projesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="5df66-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="5df66-119">CLı kullanarak bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="5df66-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="5df66-120">Bir bağımlılık eklemek için aşağıdaki örnekte gösterildiği [dotnet add package](dotnet-add-package.md) gibi komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5df66-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="5df66-121">Proje dosyasını düzenleyerek bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="5df66-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="5df66-122">Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5df66-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="5df66-123">CLı kullanarak bir bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="5df66-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="5df66-124">Bir bağımlılığı kaldırmak için, aşağıdaki örnekte [dotnet remove package](dotnet-remove-package.md) gösterildiği gibi komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5df66-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="5df66-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5df66-125">See also</span></span>

* [<span data-ttu-id="5df66-126">Proje dosyalarında paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="5df66-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties)
* <span data-ttu-id="5df66-127">[dotnet list packagekomutundaki](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="5df66-127">[dotnet list package command](dotnet-remove-package.md)</span></span>

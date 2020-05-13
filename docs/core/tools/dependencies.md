---
title: .NET Core 'da bağımlılıkları yönetme
description: Bir .NET Core uygulaması için proje bağımlılıklarının nasıl yönetileceğini açıklar.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: b77acc7d4f03a45784f753d3daaa9810f110a6ac
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205949"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="1f368-103">.NET Core uygulamalarında bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="1f368-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="1f368-104">Bu makalede, proje dosyasını düzenleyerek veya CLı kullanarak bağımlılık ekleme ve kaldırma işlemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f368-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="1f368-105">\<Packagereference> öğesi</span><span class="sxs-lookup"><span data-stu-id="1f368-105">The \<PackageReference> element</span></span>

<span data-ttu-id="1f368-106">`<PackageReference>`Proje dosyası öğesi aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1f368-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="1f368-107">`Include`Öznitelik, projeye eklenecek PAKETIN kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f368-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="1f368-108">`Version`Öznitelik alınacak sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f368-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="1f368-109">Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1f368-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="1f368-110">Proje dosyası söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1f368-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="1f368-111">Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:</span><span class="sxs-lookup"><span data-stu-id="1f368-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="1f368-112">Önceki örnekteki bağımlılık yalnızca derleme söz konusu hedef için varsa geçerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f368-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="1f368-113">`$(TargetFramework)`Koşulunda, projede ayarlanmış bir MSBuild özelliği bulunur.</span><span class="sxs-lookup"><span data-stu-id="1f368-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="1f368-114">En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1f368-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="1f368-115">Proje dosyasını düzenleyerek bir bağımlılık ekleyin</span><span class="sxs-lookup"><span data-stu-id="1f368-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="1f368-116">Bir bağımlılık eklemek için bir `<PackageReference>` öğe içine bir öğe ekleyin `<ItemGroup>` .</span><span class="sxs-lookup"><span data-stu-id="1f368-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="1f368-117">Var olan bir `<ItemGroup>` veya yeni bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f368-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="1f368-118">Aşağıdaki örnek, tarafından oluşturulan varsayılan konsol uygulaması projesini kullanır `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="1f368-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="1f368-119">CLı kullanarak bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="1f368-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="1f368-120">Bir bağımlılık eklemek için [dotnet add package](dotnet-add-package.md) Aşağıdaki örnekte gösterildiği gibi komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1f368-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="1f368-121">Proje dosyasını düzenleyerek bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="1f368-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="1f368-122">Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1f368-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="1f368-123">CLı kullanarak bir bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="1f368-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="1f368-124">Bir bağımlılığı kaldırmak için, [dotnet remove package](dotnet-remove-package.md) Aşağıdaki örnekte gösterildiği gibi komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1f368-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="1f368-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f368-125">See also</span></span>

* [<span data-ttu-id="1f368-126">Proje dosyalarında paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="1f368-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* <span data-ttu-id="1f368-127">[dotnet list packagekomutundaki](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="1f368-127">[dotnet list package command](dotnet-remove-package.md)</span></span>

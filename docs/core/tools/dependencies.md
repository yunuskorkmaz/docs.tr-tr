---
title: ''
description: ''
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: ''
ms.openlocfilehash: 667b2d4d68edd82a4d18c370e45ea18f4d4b379a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702846"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="d9d40-101">.NET Core uygulamalarında bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="d9d40-101">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="d9d40-102">Bu makalede, proje dosyasını düzenleyerek veya CLı kullanarak bağımlılık ekleme ve kaldırma işlemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9d40-102">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="d9d40-103">\<Packagereference> öğesi</span><span class="sxs-lookup"><span data-stu-id="d9d40-103">The \<PackageReference> element</span></span>

<span data-ttu-id="d9d40-104">`<PackageReference>`Proje dosyası öğesi aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d9d40-104">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="d9d40-105">`Include`Öznitelik, projeye eklenecek PAKETIN kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9d40-105">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="d9d40-106">`Version`Öznitelik alınacak sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9d40-106">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="d9d40-107">Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9d40-107">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="d9d40-108">Proje dosyası söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="d9d40-108">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="d9d40-109">Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:</span><span class="sxs-lookup"><span data-stu-id="d9d40-109">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="d9d40-110">Önceki örnekteki bağımlılık yalnızca derleme söz konusu hedef için varsa geçerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d9d40-110">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="d9d40-111">`$(TargetFramework)`Koşulunda, projede ayarlanmış bir MSBuild özelliği bulunur.</span><span class="sxs-lookup"><span data-stu-id="d9d40-111">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="d9d40-112">En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d9d40-112">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="d9d40-113">Proje dosyasını düzenleyerek bir bağımlılık ekleyin</span><span class="sxs-lookup"><span data-stu-id="d9d40-113">Add a dependency by editing the project file</span></span>

<span data-ttu-id="d9d40-114">Bir bağımlılık eklemek için bir `<PackageReference>` öğe içine bir öğe ekleyin `<ItemGroup>` .</span><span class="sxs-lookup"><span data-stu-id="d9d40-114">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="d9d40-115">Var olan bir `<ItemGroup>` veya yeni bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9d40-115">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="d9d40-116">Aşağıdaki örnek, tarafından oluşturulan varsayılan konsol uygulaması projesini kullanır `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="d9d40-116">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="d9d40-117">CLı kullanarak bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="d9d40-117">Add a dependency by using the CLI</span></span>

<span data-ttu-id="d9d40-118">Bir bağımlılık eklemek için [dotnet add package](dotnet-add-package.md) Aşağıdaki örnekte gösterildiği gibi komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d9d40-118">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="d9d40-119">Proje dosyasını düzenleyerek bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="d9d40-119">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="d9d40-120">Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d9d40-120">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="d9d40-121">CLı kullanarak bir bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="d9d40-121">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="d9d40-122">Bir bağımlılığı kaldırmak için, [dotnet remove package](dotnet-remove-package.md) Aşağıdaki örnekte gösterildiği gibi komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d9d40-122">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="d9d40-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9d40-123">See also</span></span>

* [<span data-ttu-id="d9d40-124">Proje dosyalarında paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="d9d40-124">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* <span data-ttu-id="d9d40-125">[dotnet list packagekomutundaki](dotnet-list-package.md)</span><span class="sxs-lookup"><span data-stu-id="d9d40-125">[dotnet list package command](dotnet-list-package.md)</span></span>

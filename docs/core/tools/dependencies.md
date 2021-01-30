---
title: .NET 'teki bağımlılıkları yönetme
description: Bir .NET uygulaması için proje bağımlılıklarının nasıl yönetileceğini açıklar.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.topic: how-to
ms.date: 01/28/2021
ms.openlocfilehash: 9f5f814d0b4dc7aa3ff1a938c172475169a55bf2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216134"
---
# <a name="manage-dependencies-in-net-applications"></a><span data-ttu-id="19ed1-103">.NET uygulamalarında bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="19ed1-103">Manage dependencies in .NET applications</span></span>

<span data-ttu-id="19ed1-104">Bu makalede, proje dosyasını düzenleyerek veya CLı kullanarak bağımlılık ekleme ve kaldırma işlemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19ed1-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="19ed1-105">\<PackageReference>Öğe</span><span class="sxs-lookup"><span data-stu-id="19ed1-105">The \<PackageReference> element</span></span>

<span data-ttu-id="19ed1-106">`<PackageReference>`Proje dosyası öğesi aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="19ed1-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="19ed1-107">`Include`Öznitelik, projeye eklenecek PAKETIN kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19ed1-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="19ed1-108">`Version`Öznitelik alınacak sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="19ed1-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="19ed1-109">Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="19ed1-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="19ed1-110">Proje dosyası söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="19ed1-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="19ed1-111">Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:</span><span class="sxs-lookup"><span data-stu-id="19ed1-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="19ed1-112">Önceki örnekteki bağımlılık yalnızca derleme söz konusu hedef için varsa geçerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="19ed1-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="19ed1-113">`$(TargetFramework)`Koşulunda, projede ayarlanmış bir MSBuild özelliği bulunur.</span><span class="sxs-lookup"><span data-stu-id="19ed1-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="19ed1-114">En yaygın .NET uygulamaları için bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="19ed1-114">For most common .NET applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="19ed1-115">Proje dosyasını düzenleyerek bir bağımlılık ekleyin</span><span class="sxs-lookup"><span data-stu-id="19ed1-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="19ed1-116">Bir bağımlılık eklemek için bir `<PackageReference>` öğe içine bir öğe ekleyin `<ItemGroup>` .</span><span class="sxs-lookup"><span data-stu-id="19ed1-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="19ed1-117">Var olan bir `<ItemGroup>` veya yeni bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19ed1-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="19ed1-118">Aşağıdaki örnek, tarafından oluşturulan varsayılan konsol uygulaması projesini kullanır `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="19ed1-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="19ed1-119">CLı kullanarak bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="19ed1-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="19ed1-120">Bir bağımlılık eklemek için [dotnet add package](dotnet-add-package.md) Aşağıdaki örnekte gösterildiği gibi komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="19ed1-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="19ed1-121">Proje dosyasını düzenleyerek bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="19ed1-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="19ed1-122">Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.</span><span class="sxs-lookup"><span data-stu-id="19ed1-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="19ed1-123">CLı kullanarak bir bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="19ed1-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="19ed1-124">Bir bağımlılığı kaldırmak için, [dotnet remove package](dotnet-remove-package.md) Aşağıdaki örnekte gösterildiği gibi komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="19ed1-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="19ed1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19ed1-125">See also</span></span>

* [<span data-ttu-id="19ed1-126">Proje dosyalarında paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="19ed1-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [<span data-ttu-id="19ed1-127">dotnet list package komutundaki</span><span class="sxs-lookup"><span data-stu-id="19ed1-127">dotnet list package command</span></span>](dotnet-list-package.md)

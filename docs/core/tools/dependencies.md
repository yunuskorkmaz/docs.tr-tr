---
title: .NET Core'daki bağımlılıkları yönetme
description: .NET Core uygulaması için proje bağımlılıklarının nasıl yönetilmeye başlanması gerektiğini açıklar.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399149"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="1f86f-103">.NET Core uygulamalarındaki bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="1f86f-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="1f86f-104">Bu makalede, proje dosyasını düzenleyerek veya CLI'yi kullanarak bağımlılıkların nasıl ekleyeceğinive kaldırılacakları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f86f-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="1f86f-105">\<PackageReference> öğesi</span><span class="sxs-lookup"><span data-stu-id="1f86f-105">The \<PackageReference> element</span></span>

<span data-ttu-id="1f86f-106">`<PackageReference>` Proje dosyası öğesi aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1f86f-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="1f86f-107">Öznitelik, `Include` projeye eklenecek paketin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f86f-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="1f86f-108">Öznitelik, `Version` elde etmek için sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f86f-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="1f86f-109">Sürümler [NuGet sürüm kurallarına](/nuget/create-packages/dependency-versions#version-ranges)göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1f86f-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="1f86f-110">Proje dosyası sözdizimini bilmiyorsanız, daha fazla bilgi için [MSBuild proje başvuru](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1f86f-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="1f86f-111">Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:</span><span class="sxs-lookup"><span data-stu-id="1f86f-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="1f86f-112">Önceki örnekteki bağımlılık, yalnızca bu hedef için yapı gerçekleşiyorsa geçerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f86f-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="1f86f-113">Durumda `$(TargetFramework)` projede ayarlanan bir MSBuild özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="1f86f-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="1f86f-114">En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1f86f-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="1f86f-115">Proje dosyasını düzenleyerek bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="1f86f-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="1f86f-116">Bağımlılık eklemek için, bir `<PackageReference>` `<ItemGroup>` öğenin içine bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f86f-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="1f86f-117">Varolan `<ItemGroup>` bir taneye ekleyebilir veya yeni bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f86f-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="1f86f-118">Aşağıdaki örnekte, aşağıdakiler tarafından `dotnet new console`oluşturulan varsayılan konsol uygulama projesi kullanır:</span><span class="sxs-lookup"><span data-stu-id="1f86f-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="1f86f-119">CLI'yi kullanarak bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="1f86f-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="1f86f-120">Bağımlılık eklemek için aşağıdaki [dotnet add package](dotnet-add-package.md) örnekte gösterildiği gibi komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1f86f-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="1f86f-121">Proje dosyasını düzenleyerek bir bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="1f86f-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="1f86f-122">Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1f86f-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="1f86f-123">CLI'yi kullanarak bir bağımlılığı kaldırma</span><span class="sxs-lookup"><span data-stu-id="1f86f-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="1f86f-124">Bir bağımlılığı kaldırmak için [dotnet remove package](dotnet-remove-package.md) aşağıdaki örnekte gösterildiği gibi komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1f86f-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="1f86f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f86f-125">See also</span></span>

* [<span data-ttu-id="1f86f-126">Proje dosyalarındaki Paketleri NuGet</span><span class="sxs-lookup"><span data-stu-id="1f86f-126">NuGet packages in project files</span></span>](../project-sdk/msbuild-props.md#nuget-packages)
* <span data-ttu-id="1f86f-127">[dotnet list packageKomut](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="1f86f-127">[dotnet list package command](dotnet-remove-package.md)</span></span>

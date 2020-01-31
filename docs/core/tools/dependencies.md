---
title: .NET Core araçları 'nda bağımlılıkları yönetme
description: .NET Core araçlarıyla bağımlılıklarınızın nasıl yönetileceğini açıklar.
ms.date: 03/06/2017
ms.openlocfilehash: 28280dc05e746cdef4e90870cd4cb528382c45bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787870"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="ff0ea-103">.NET Core SDK 1,0 ile bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="ff0ea-103">Manage dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="ff0ea-104">.NET Core projelerinin Project. json ' dan csproj ve MSBuild 'e taşınması sayesinde, proje dosyası ve bağımlılık izlemeye izin veren varlıkların birleşme ile sonuçlanan önemli bir yatırım gerçekleşsin.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="ff0ea-105">.NET Core projeleri için bu, Project. JSON öğesine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-105">For .NET Core projects, this is similar to what project.json did.</span></span> <span data-ttu-id="ff0ea-106">NuGet bağımlılıklarını izleyen ayrı bir JSON veya XML dosyası yoktur.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="ff0ea-107">Bu değişiklik ile, `<PackageReference>`adlı csproj sözdizimine başka bir *başvuru* türü de sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span>

<span data-ttu-id="ff0ea-108">Bu belgede yeni başvuru türü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-108">This document describes the new reference type.</span></span> <span data-ttu-id="ff0ea-109">Ayrıca, bu yeni başvuru türünü kullanarak projenize nasıl bir paket bağımlılığı ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-109">It also shows how to add a package dependency using this new reference type to your project.</span></span>

## <a name="the-new-packagereference-element"></a><span data-ttu-id="ff0ea-110">Yeni \<PackageReference > öğesi</span><span class="sxs-lookup"><span data-stu-id="ff0ea-110">The new \<PackageReference> element</span></span>

<span data-ttu-id="ff0ea-111">`<PackageReference>` aşağıdaki temel yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ff0ea-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="ff0ea-112">MSBuild hakkında bilginiz varsa, zaten mevcut olan diğer başvuru türlerine tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="ff0ea-113">Bu anahtar, projeye eklemek istediğiniz paket kimliğini belirten `Include` deyimidir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-113">The key is the `Include` statement, which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="ff0ea-114">`<Version>` Child öğesi alınacak sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="ff0ea-115">Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="ff0ea-116">Genel `csproj` söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="ff0ea-117">Yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek aşağıdaki örnekteki gibi koşullar kullanılarak yapılır:</span><span class="sxs-lookup"><span data-stu-id="ff0ea-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="ff0ea-118">Yukarıdaki, bağımlılık yalnızca söz konusu hedef için derleme gerçekleşince geçerli olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="ff0ea-119">Koşuldaki `$(TargetFramework)`, projede ayarlanan MSBuild özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-119">The `$(TargetFramework)` in the condition is an MSBuild property that is being set in the project.</span></span> <span data-ttu-id="ff0ea-120">En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-120">For most common .NET Core applications, you will not need to do this.</span></span>

## <a name="add-a-dependency-to-the-project"></a><span data-ttu-id="ff0ea-121">Projeye bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="ff0ea-121">Add a dependency to the project</span></span>

<span data-ttu-id="ff0ea-122">Projenize bağımlılık eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="ff0ea-123">Projenize Json.NET Version `9.0.1` eklemenin bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="ff0ea-124">Tabii ki, diğer herhangi bir NuGet bağımlılığı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-124">Of course, it is applicable to any other NuGet dependency.</span></span>

<span data-ttu-id="ff0ea-125">Proje dosyanızı açtığınızda, iki veya daha fazla `<ItemGroup>` düğümü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="ff0ea-126">Düğümlerden birinin zaten `<PackageReference>` öğeleri olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="ff0ea-127">Yeni bağımlılığı bu düğüme ekleyebilir veya yeni bir tane oluşturabilirsiniz; Sonuç aynı olacağı için size ait.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-127">You can add your new dependency to this node, or create a new one; it is up to you, as the result will be the same.</span></span>

<span data-ttu-id="ff0ea-128">Aşağıdaki örnek, `dotnet new console`tarafından bırakılan varsayılan şablonu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-128">The following example uses the default template that's dropped by `dotnet new console`.</span></span> <span data-ttu-id="ff0ea-129">Bu basit bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-129">This is a simple console application.</span></span> <span data-ttu-id="ff0ea-130">Projeyi açtığınızda, içinde zaten var olan `<PackageReference>` `<ItemGroup>` bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-130">When you open up the project, you'll find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="ff0ea-131">Aşağıdaki öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ff0ea-131">Add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="ff0ea-132">Bundan sonra, projeyi kaydedin ve bağımlılığı yüklemek için `dotnet restore` komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-132">After this, save the project and run the `dotnet restore` command to install the dependency.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="ff0ea-133">Tam proje şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="ff0ea-133">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="remove-a-dependency-from-the-project"></a><span data-ttu-id="ff0ea-134">Bir bağımlılığı projeden kaldırma</span><span class="sxs-lookup"><span data-stu-id="ff0ea-134">Remove a dependency from the project</span></span>

<span data-ttu-id="ff0ea-135">Proje dosyasından bir bağımlılığı kaldırmak, `<PackageReference>` proje dosyasından kaldırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="ff0ea-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>

---
title: .NET Core araçları 'nda bağımlılıkları yönetme
description: .NET Core araçlarıyla bağımlılıklarınızın nasıl yönetileceğini açıklar.
ms.date: 03/06/2017
ms.openlocfilehash: e14fa42534d807e2a0fcce1dabe747c18c5166b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733380"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="5597c-103">.NET Core SDK 1,0 ile bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="5597c-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="5597c-104">.NET Core projelerinin Project. json ' dan csproj ve MSBuild 'e taşınması sayesinde, proje dosyası ve bağımlılık izlemeye izin veren varlıkların birleşme ile sonuçlanan önemli bir yatırım gerçekleşsin.</span><span class="sxs-lookup"><span data-stu-id="5597c-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="5597c-105">.NET Core projeleri için bu, Project. JSON ile benzerdir.</span><span class="sxs-lookup"><span data-stu-id="5597c-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="5597c-106">NuGet bağımlılıklarını izleyen ayrı bir JSON veya XML dosyası yoktur.</span><span class="sxs-lookup"><span data-stu-id="5597c-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="5597c-107">Bu değişiklik ile, `<PackageReference>`adlı csproj sözdizimine başka bir *başvuru* türü de sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="5597c-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="5597c-108">Bu belgede yeni başvuru türü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5597c-108">This document describes the new reference type.</span></span> <span data-ttu-id="5597c-109">Ayrıca, bu yeni başvuru türünü kullanarak projenize nasıl bir paket bağımlılığı ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5597c-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="5597c-110">Yeni \<PackageReference > öğesi</span><span class="sxs-lookup"><span data-stu-id="5597c-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="5597c-111">`<PackageReference>` aşağıdaki temel yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5597c-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="5597c-112">MSBuild hakkında bilginiz varsa, zaten mevcut olan diğer başvuru türlerine tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="5597c-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="5597c-113">Anahtar, projeye eklemek istediğiniz paket kimliğini belirten `Include` deyimidir.</span><span class="sxs-lookup"><span data-stu-id="5597c-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="5597c-114">`<Version>` Child öğesi alınacak sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5597c-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="5597c-115">Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5597c-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="5597c-116">Genel `csproj` söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5597c-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="5597c-117">Yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek aşağıdaki örnekteki gibi koşullar kullanılarak yapılır:</span><span class="sxs-lookup"><span data-stu-id="5597c-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="5597c-118">Yukarıdaki, bağımlılık yalnızca söz konusu hedef için derleme gerçekleşince geçerli olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5597c-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="5597c-119">Koşuldaki `$(TargetFramework)`, projede ayarlanan MSBuild özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="5597c-119">The `$(TargetFramework)` in the condition is an MSBuild property that is being set in the project.</span></span> <span data-ttu-id="5597c-120">En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5597c-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="5597c-121">Projenize bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="5597c-121">Adding a dependency to your project</span></span>
<span data-ttu-id="5597c-122">Projenize bağımlılık eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="5597c-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="5597c-123">Projenize Json.NET Version `9.0.1` eklemenin bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5597c-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="5597c-124">Tabii ki, diğer herhangi bir NuGet bağımlılığı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5597c-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="5597c-125">Proje dosyanızı açtığınızda, iki veya daha fazla `<ItemGroup>` düğümü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5597c-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="5597c-126">Düğümlerden birinin zaten `<PackageReference>` öğeleri olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5597c-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="5597c-127">Yeni bağımlılığı bu düğüme ekleyebilir veya yeni bir tane oluşturabilirsiniz; Sonuç aynı olacağı için tamamen size kadar sürer.</span><span class="sxs-lookup"><span data-stu-id="5597c-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="5597c-128">Bu örnekte, `dotnet new console`tarafından bırakılan varsayılan şablonu kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="5597c-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="5597c-129">Bu basit bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5597c-129">This is a simple console application.</span></span> <span data-ttu-id="5597c-130">Projeyi açtıklarında, ilk olarak zaten var olan `<PackageReference>` `<ItemGroup>` bulduk.</span><span class="sxs-lookup"><span data-stu-id="5597c-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="5597c-131">Daha sonra aşağıdaki öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5597c-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="5597c-132">Bundan sonra, projeyi kaydeder ve bağımlılığı yüklemek için `dotnet restore` komutunu çalıştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="5597c-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="5597c-133">Tam proje şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="5597c-133">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="5597c-134">Bir bağımlılığı projeden kaldırma</span><span class="sxs-lookup"><span data-stu-id="5597c-134">Removing a dependency from the project</span></span>
<span data-ttu-id="5597c-135">Proje dosyasından bir bağımlılığı kaldırmak, `<PackageReference>` proje dosyasından kaldırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="5597c-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>

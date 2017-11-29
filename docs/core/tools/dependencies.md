---
title: ".NET Core araç bağımlılıkları yönetme"
description: "Bağımlılıklarınız .NET Core araçları ile yönetmek açıklanmaktadır."
keywords: "CLI, genişletilebilirlik, özel komutlar, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
ms.openlocfilehash: 21f42bbf4693c78a5be271b7769ef4489ed6d476
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="70248-104">Bağımlılıkları .NET Core SDK 1.0 ile yönetme</span><span class="sxs-lookup"><span data-stu-id="70248-104">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="70248-105">Önemli bir yatırımın, taşımak .NET Core projeleri ile project.json csproj ve MSBuild, proje dosyası ve bağımlılıkları izleme izin varlıklar Birleştirici içinde sonuçlanan ayrıca oluştu.</span><span class="sxs-lookup"><span data-stu-id="70248-105">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="70248-106">.NET Core projelerde bu hangi project.json vermedi için benzer.</span><span class="sxs-lookup"><span data-stu-id="70248-106">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="70248-107">NuGet bağımlılıkları izleyen ayrı JSON veya XML dosya yok.</span><span class="sxs-lookup"><span data-stu-id="70248-107">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="70248-108">Bu değişiklikle, biz de başka bir tür ekledik *başvuru* adlı csproj sözdizimi içine `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="70248-108">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="70248-109">Bu belgede yeni başvuru türü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70248-109">This document describes the new reference type.</span></span> <span data-ttu-id="70248-110">Ayrıca, bu yeni başvuru türü projenize kullanarak bir paket bağımlılığı eklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="70248-110">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="70248-111">Yeni \<PackageReference > öğesi</span><span class="sxs-lookup"><span data-stu-id="70248-111">The new \<PackageReference> element</span></span>
<span data-ttu-id="70248-112">`<PackageReference>` Aşağıdaki temel yapı vardır:</span><span class="sxs-lookup"><span data-stu-id="70248-112">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="70248-113">MSBuild ile hakkında bilginiz varsa, zaten bulunan diğer başvuru türleri için tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="70248-113">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="70248-114">Anahtar `Include` deyimi projeye eklemek istediğiniz paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="70248-114">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="70248-115">`<Version>` Alt öğesi almak için sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="70248-115">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="70248-116">Sürümleri göre belirtilen [NuGet sürümü kurallarını](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="70248-116">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="70248-117">Bütün ile bilmiyorsanız `csproj` sözdizimi, bkz: [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="70248-117">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="70248-118">Yalnızca belirli bir hedef olarak kullanılabilir bir bağımlılık ekleme gerçekleştirilir gibi koşullar aşağıdaki örnekte kullanarak:</span><span class="sxs-lookup"><span data-stu-id="70248-118">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

<span data-ttu-id="70248-119">Bağımlılık yalnızca derleme için hedef verilen oluşuyorsa geçerli olacağını yukarıdaki anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="70248-119">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="70248-120">`$(TargetFramework)` Koşulunda projede ayarlandığında bir MSBuild özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="70248-120">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="70248-121">En yaygın .NET Core uygulamalar için bunu yapmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="70248-121">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="70248-122">Projenize bir bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="70248-122">Adding a dependency to your project</span></span>
<span data-ttu-id="70248-123">Projenize bir bağımlılık ekleme basittir.</span><span class="sxs-lookup"><span data-stu-id="70248-123">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="70248-124">Json.NET sürüm ekleme konusunda bir örneği burada verilmiştir `9.0.1` projenize.</span><span class="sxs-lookup"><span data-stu-id="70248-124">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="70248-125">Elbette, herhangi bir NuGet bağımlılığı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="70248-125">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="70248-126">Proje dosyası açtığınızda, iki veya daha fazla görürsünüz `<ItemGroup>` düğümleri.</span><span class="sxs-lookup"><span data-stu-id="70248-126">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="70248-127">Düğümlerden birinde zaten olduğunu fark edeceksiniz `<PackageReference>` öğelere.</span><span class="sxs-lookup"><span data-stu-id="70248-127">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="70248-128">Bu düğüm, yeni bağımlılık ekleme ya da yeni bir tane oluşturun; Sonuç aynı olacak şekilde, tamamen size bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="70248-128">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="70248-129">Bu örnekte bırakılan tarafından varsayılan şablonu kullanacağız `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="70248-129">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="70248-130">Basit bir konsol uygulaması budur.</span><span class="sxs-lookup"><span data-stu-id="70248-130">This is a simple console application.</span></span> <span data-ttu-id="70248-131">Biz projeyi açtığınızda, biz ilk Bul `<ItemGroup>` zaten var olan `<PackageReference>` da.</span><span class="sxs-lookup"><span data-stu-id="70248-131">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="70248-132">Biz ardından aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="70248-132">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="70248-133">Bundan sonra biz projeyi kaydedin ve Çalıştır `dotnet restore` bağımlılık yüklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="70248-133">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="70248-134">Tam proje şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="70248-134">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="70248-135">Bir bağımlılık projeden kaldırma</span><span class="sxs-lookup"><span data-stu-id="70248-135">Removing a dependency from the project</span></span>
<span data-ttu-id="70248-136">Proje dosyasından bir bağımlılık kaldırmayı içerir yalnızca kaldırma `<PackageReference>` proje dosyasından.</span><span class="sxs-lookup"><span data-stu-id="70248-136">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>

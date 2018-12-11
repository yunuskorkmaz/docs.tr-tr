---
title: .NET Core 1.0 için paket bağımlılığı sürümlerini yönetme
description: .NET Core kitaplıkları ve uygulamaları için paket bağımlılık sürüm yönetimi hakkında bilgi edinin.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 7d7133ddb8717db1b830e531955454925c31a728
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168617"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="dc4df-103">.NET Core 1.0 için paket bağımlılığı sürümlerini yönetme</span><span class="sxs-lookup"><span data-stu-id="dc4df-103">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="dc4df-104">Bu makale, .NET Core kitaplıkları ve uygulamaları için paket sürümleri hakkında bilmeniz gerekenler kapsar.</span><span class="sxs-lookup"><span data-stu-id="dc4df-104">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="dc4df-105">Sözlük</span><span class="sxs-lookup"><span data-stu-id="dc4df-105">Glossary</span></span>

<span data-ttu-id="dc4df-106">**Düzeltme** -bağımlılıkları düzeltme kullanmakta olduğunuz NuGet üzerinde .NET Core 1.0 için yayımlanan paket aynı "ailesi" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dc4df-106">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="dc4df-107">**Metapackage** -NuGet paketlerini kümesini temsil eden bir NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="dc4df-107">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="dc4df-108">**Kırpma** -bir metapackage, bağımlı değildir paketlerini kaldırma işlemi.</span><span class="sxs-lookup"><span data-stu-id="dc4df-108">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="dc4df-109">NuGet paketi yazarları için ilgili bir sorun budur.</span><span class="sxs-lookup"><span data-stu-id="dc4df-109">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="dc4df-110">Bkz: [azaltma Paket bağımlılıklarını project.json ile](../deploying/reducing-dependencies.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="dc4df-110">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="dc4df-111">.NET Core 1.0 için bağımlılıklarınızı düzeltme</span><span class="sxs-lookup"><span data-stu-id="dc4df-111">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="dc4df-112">Güvenilir bir şekilde paketlerini geri yükleyip güvenilir kod yazma için bağımlılıklarınızı yanı sıra .NET Core 1.0 sevkiyat paketleri sürümlerine düzeltmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="dc4df-112">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="dc4df-113">Başka bir deyişle, her paketi, hiçbir ek niteleyicileri tek bir sürüm gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc4df-113">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="dc4df-114">**1.0 sabit paketleri örnekleri**</span><span class="sxs-lookup"><span data-stu-id="dc4df-114">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="dc4df-115">**1.0 düzeltilmez paketleri örnekleri**</span><span class="sxs-lookup"><span data-stu-id="dc4df-115">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="dc4df-116">Bu neden önemlidir?</span><span class="sxs-lookup"><span data-stu-id="dc4df-116">Why does this matter?</span></span>

<span data-ttu-id="dc4df-117">Bağımlılıklarınızı hangi gemileri birlikte .NET Core 1.0 için düzeltme varsa, bu paketleri tüm birlikte çalışacağından emin ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="dc4df-117">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="dc4df-118">Bu şekilde sabit olmayan paketler kullanırsanız, böyle bir garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="dc4df-118">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="dc4df-119">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="dc4df-119">Scenarios</span></span>

<span data-ttu-id="dc4df-120">Tüm paketleri ve bunların sürümlerini .NET Core 1.0 ile yayımlanan büyük bir listesi olmasa da, kodunuzun belirli senaryolarda düşerse içinden aramak sahip.</span><span class="sxs-lookup"><span data-stu-id="dc4df-120">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="dc4df-121">**Yalnızca bağlı olan** `NETStandard.Library` **?**</span><span class="sxs-lookup"><span data-stu-id="dc4df-121">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="dc4df-122">Bu nedenle, düzeltmeniz durumunda, `NETStandard.Library` paket sürümüne `1.6`.</span><span class="sxs-lookup"><span data-stu-id="dc4df-122">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="dc4df-123">Bu seçkin metapackage olduğu için paket kapanış ayrıca 1.0 sabit.</span><span class="sxs-lookup"><span data-stu-id="dc4df-123">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="dc4df-124">**Yalnızca bağlı olan** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="dc4df-124">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="dc4df-125">Bu nedenle, düzeltmeniz durumunda, `Microsoft.NETCore.App` paket sürümüne `1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="dc4df-125">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="dc4df-126">Bu seçkin metapackage olduğu için paket kapanış ayrıca 1.0 sabit.</span><span class="sxs-lookup"><span data-stu-id="dc4df-126">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="dc4df-127">**İşiniz [kırpmayı](../deploying/reducing-dependencies.md) ,** `NETStandard.Library` **veya** `Microsoft.NETCore.App` **metapackage bağımlılıkları?**</span><span class="sxs-lookup"><span data-stu-id="dc4df-127">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="dc4df-128">Bu durumda, 1.0 ile başlamanız metapackage düzeltildiğini emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc4df-128">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="dc4df-129">Kırpma sonra bağlı tek paketler de 1.0 için sabittir.</span><span class="sxs-lookup"><span data-stu-id="dc4df-129">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="dc4df-130">**Paketleri dışında bağlı olduğunuz** `NETStandard.Library` **veya** `Microsoft.NETCore.App` **meta paketler?**</span><span class="sxs-lookup"><span data-stu-id="dc4df-130">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="dc4df-131">Bu durumda, diğer bağımlılıklarınızı 1.0 için düzeltme gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc4df-131">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="dc4df-132">Doğru paket sürümlerini görmek ve yapı numaralarını bu makalenin sonunda.</span><span class="sxs-lookup"><span data-stu-id="dc4df-132">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="dc4df-133">Bir bölme dize kullanma hakkında bir not (\*), sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc4df-133">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="dc4df-134">Bir bölme kullandığı sürüm oluşturma düzeni benimseyen (\*) dizesi: `"System.Collections":"4.0.11-*"`.</span><span class="sxs-lookup"><span data-stu-id="dc4df-134">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="dc4df-135">**Bunu**.</span><span class="sxs-lookup"><span data-stu-id="dc4df-135">**You should not do this**.</span></span>  <span data-ttu-id="dc4df-136">Bir bölme dize kullanarak farklı derlemelerden bazıları daha .NET Core 1.0 boyunca olabilir paketleri geri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc4df-136">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="dc4df-137">Bu, ardından uyumsuz olan bazı paketlerde neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc4df-137">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="dc4df-138">Paketler ve sürüm numaraları Metapackage tarafından düzenlenmiştir</span><span class="sxs-lookup"><span data-stu-id="dc4df-138">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="dc4df-139">[Tüm .NET Standard paketleri ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="dc4df-139">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="dc4df-140">[Tüm çalışma zamanı paketlerini ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="dc4df-140">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="dc4df-141">[Tüm .NET Core uygulama paketlerini ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="dc4df-141">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>

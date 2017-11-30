---
title: ".NET Core 1.0 paket bağımlılık sürümlerini yönetme"
description: ".NET Core kitaplıkları ve uygulamalar için paket bağımlılık sürüm yönetimi hakkında bilgi edinin."
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
ms.openlocfilehash: b0d4082d020da782b334a5b3999905f7de744e64
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2017
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="6e2ff-104">.NET Core 1.0 paket bağımlılık sürümlerini yönetme</span><span class="sxs-lookup"><span data-stu-id="6e2ff-104">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="6e2ff-105">Bu makalede, .NET Core kitaplıkları ve uygulamalar için paket sürümleri hakkında bilmeniz gerekenleri yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-105">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="6e2ff-106">Sözlük</span><span class="sxs-lookup"><span data-stu-id="6e2ff-106">Glossary</span></span>

<span data-ttu-id="6e2ff-107">**Düzeltme** -bağımlılıkları düzelttikten kullanmakta olduğunuz NuGet üzerinde .NET Core 1.0 için yayımlanan paket aynı "ailesi" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-107">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="6e2ff-108">**Metapackage** -NuGet paket kümesini temsil eden bir NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-108">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="6e2ff-109">**Kırpma** -metapackage, bağımlı değildir paketlerini kaldırma eylemi.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-109">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="6e2ff-110">Bu NuGet paketi yazarları için ilgili bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-110">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="6e2ff-111">Bkz: [paket bağımlılıklarıyla küçültme project.json](../deploying/reducing-dependencies.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-111">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="6e2ff-112">Bağımlılıklarınız .NET Core 1.0 için düzeltme</span><span class="sxs-lookup"><span data-stu-id="6e2ff-112">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="6e2ff-113">Güvenilir bir şekilde paketleri geri yükleyin ve güvenilir kod yazma için bağımlılıklarınızı .NET Core 1.0 sevkiyat paketleri sürümlerine düzeltmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-113">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="6e2ff-114">Başka bir deyişle, her paketi hiçbir ek niteleyicileri ile tek bir sürümü gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-114">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="6e2ff-115">**1.0 sabit paketleri örnekleri**</span><span class="sxs-lookup"><span data-stu-id="6e2ff-115">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="6e2ff-116">**1.0 düzeltilmez paketleri örnekleri**</span><span class="sxs-lookup"><span data-stu-id="6e2ff-116">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="6e2ff-117">Bu neden önemli?</span><span class="sxs-lookup"><span data-stu-id="6e2ff-117">Why does this matter?</span></span>

<span data-ttu-id="6e2ff-118">.NET Core 1.0 yanı sıra hangi gelir, bağımlılıkları düzeltin, bu paketleri tüm birlikte çalışacağını garanti ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-118">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="6e2ff-119">Bu şekilde sabit olmayan paketleri kullanıyorsanız, bu tür bir garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-119">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="6e2ff-120">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="6e2ff-120">Scenarios</span></span>

<span data-ttu-id="6e2ff-121">Tüm paketler ve .NET Core 1.0 ile yayımlanan sürümlerine büyük listesini olsa da, kodunuzu belirli senaryolarda düşerse üzerinden aramak olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-121">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="6e2ff-122">**Yalnızca bağlı olan** `NETStandard.Library` **?**</span><span class="sxs-lookup"><span data-stu-id="6e2ff-122">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="6e2ff-123">Bu nedenle, düzeltmelidir varsa, `NETStandard.Library` paketi sürümüne `1.6`.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-123">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="6e2ff-124">Bu seçkin metapackage olduğundan, paket kapatma 1.0 de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-124">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="6e2ff-125">**Yalnızca bağlı olan** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="6e2ff-125">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="6e2ff-126">Bu nedenle, düzeltmelidir varsa, `Microsoft.NETCore.App` paketi sürümüne `1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-126">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="6e2ff-127">Bu seçkin metapackage olduğundan, paket kapatma 1.0 de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-127">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="6e2ff-128">**Olduğunuz [kırpma](../deploying/reducing-dependencies.md) ,** `NETStandard.Library` **veya** `Microsoft.NETCore.App` **metapackage bağımlılıkları?**</span><span class="sxs-lookup"><span data-stu-id="6e2ff-128">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="6e2ff-129">Bu durumda, ile başlamanız metapackage 1.0 düzeltildiğini emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-129">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="6e2ff-130">Kırpma sonra bağımlı tek paketler 1.0 de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-130">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="6e2ff-131">**Paketleri dışında bağlı olduğunuz** `NETStandard.Library` **veya** `Microsoft.NETCore.App` **metapackages?**</span><span class="sxs-lookup"><span data-stu-id="6e2ff-131">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="6e2ff-132">Öyleyse, başka bir bağımlılık 1.0 için çözmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-132">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="6e2ff-133">Ve yapı numaralarını bu makalenin sonunda doğru paket sürümlerini bakın.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-133">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="6e2ff-134">Splat dizesi kullanarak bir not (\*), sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e2ff-134">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="6e2ff-135">Bir splat kullanan bir sürüm desen benimseyen (\*) dize şuna benzer: `"System.Collections":"4.0.11-*"`.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-135">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="6e2ff-136">**Bunu**.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-136">**You should not do this**.</span></span>  <span data-ttu-id="6e2ff-137">Splat dizesi kullanılarak farklı yapılandırmalardan bazıları .NET Core 1. 0 ' daha fazla boyunca olabilir paketleri geri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-137">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="6e2ff-138">Bu, ardından uyumsuz olan bazı paketler neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ff-138">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="6e2ff-139">Paketler ve sürüm numaraları Metapackage tarafından düzenlenmiştir</span><span class="sxs-lookup"><span data-stu-id="6e2ff-139">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="6e2ff-140">[Tüm .NET standart paketleri ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="6e2ff-140">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="6e2ff-141">[Tüm çalışma zamanı paketleri ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="6e2ff-141">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="6e2ff-142">[Tüm .NET Core uygulama paketleri ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="6e2ff-142">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>

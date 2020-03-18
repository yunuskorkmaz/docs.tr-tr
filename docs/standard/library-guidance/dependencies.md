---
title: Bağımlılıklar ve .NET kitaplıkları
description: .NET kitaplıklarında NuGet bağımlılıklarını yönetmek için en iyi uygulama önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731484"
---
# <a name="dependencies"></a><span data-ttu-id="02cf3-103">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="02cf3-103">Dependencies</span></span>

<span data-ttu-id="02cf3-104">.NET kitaplığına bağımlılık eklemenin birincil yolu NuGet paketlerine başvurmaktır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="02cf3-105">NuGet paket başvuruları, önceden yazılmış işlevselliği hızla yeniden kullanmanıza ve bunlardan yararlanmanıza olanak tanır, ancak bunlar .NET geliştiricileri için ortak bir sürtünme kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="02cf3-106">Bağımlılıkları doğru yönetmek, diğer .NET kitaplıklarında yapılan değişikliklerin .NET kitaplığınızı kırmasını önlemek için önemlidir ve bunun tersi de önemlidir!</span><span class="sxs-lookup"><span data-stu-id="02cf3-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="02cf3-107">Elmas bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="02cf3-107">Diamond dependencies</span></span>

<span data-ttu-id="02cf3-108">Bir .NET projesinin bağımlılık ağacında bir paketin birden çok sürümü olması yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="02cf3-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="02cf3-109">Örneğin, bir uygulama, her biri aynı paketin farklı sürümlerine dayanan iki NuGet paketine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="02cf3-110">Uygulamanın bağımlılık grafiğinde elmas bağımlılığı artık mevcut.</span><span class="sxs-lookup"><span data-stu-id="02cf3-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="02cf3-111">![Elmas bağımlılığı](./media/dependencies/diamond-dependency.png "Elmas bağımlılığı")</span><span class="sxs-lookup"><span data-stu-id="02cf3-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="02cf3-112">Yapı zamanında NuGet, bağımlılıkların bağımlılıkları da dahil olmak üzere projenin bağlı olduğu tüm paketleri analiz eder.</span><span class="sxs-lookup"><span data-stu-id="02cf3-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="02cf3-113">Bir paketin birden çok sürümü algılandığında, bir paket seçmek için kurallar değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="02cf3-114">Bir derlemenin yan yana sürümlerini aynı uygulamada çalıştırmak .NET'te sorunlu olduğundan, paketleri birleştirme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="02cf3-115">Çoğu elmas bağımlılığı kolayca çözülür; ancak, belirli durumlarda sorunlar yaratabilirler:</span><span class="sxs-lookup"><span data-stu-id="02cf3-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="02cf3-116">**Çakışan NuGet paket başvuruları,** paket geri yüklemesi sırasında bir sürümün çözülmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="02cf3-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="02cf3-117">**Sürümler arasındaki son dakika değişiklikleri** çalışma zamanında hatalara ve özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="02cf3-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="02cf3-118">**Paket derlemesi güçlü adlandırılmış,** montaj sürümü değiştirildi ve uygulama .NET Framework üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="02cf3-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="02cf3-119">Derleme bağlama yönlendirmeleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="02cf3-120">Sizinkinin yanında hangi paketlerin kullanılacağını bilmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="02cf3-121">Kitaplığınızı kıran elmas bağımlılığı olasılığını azaltmanın iyi bir yolu, bağlı olduğunuz paket sayısını en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="02cf3-122">✔️ .NET kitaplığınızı gereksiz bağımlılıklar için gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="02cf3-122">✔️ DO review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="02cf3-123">NuGet bağımlılık sürüm aralıkları</span><span class="sxs-lookup"><span data-stu-id="02cf3-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="02cf3-124">Paket başvurusu, izin verdiği geçerli paketlerin aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="02cf3-125">Genellikle, proje dosyasındaki paket başvuru sürümü minimum sürümüdür ve en fazla sürüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="02cf3-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="02cf3-126">NuGet'in bağımlılıkları çözerken kullandığı kurallar [karmaşıktır,](/nuget/consume-packages/dependency-resolution)ancak NuGet her zaman en düşük geçerli sürümü arar.</span><span class="sxs-lookup"><span data-stu-id="02cf3-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="02cf3-127">NuGet, en düşük uyumluluk sorunları olacağından, kullanılabilir en yüksek sürümü kullanmaya göre en düşük geçerli sürümü tercih eder.</span><span class="sxs-lookup"><span data-stu-id="02cf3-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="02cf3-128">NuGet'in en düşük geçerli sürüm kuralı nedeniyle, en son sürümü almaktan kaçınmak için paket başvurularına bir üst sürüm veya tam aralık yerleştirmeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="02cf3-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="02cf3-129">NuGet zaten sizin için en düşük, en uyumlu sürümü bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="02cf3-130">Üst sürüm sınırları, bir çakışma olduğunda NuGet'in başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="02cf3-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="02cf3-131">Örneğin, bir kitaplık tam olarak 1,0'ı kabul ederken, başka bir kitaplık 2,0 veya üzeri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="02cf3-132">Sürüm 2.0'da kırılma değişiklikleri getirilmiş olsa da, katı veya üst sınır sürüm bağımlılığı bir hatayı garanti eder.</span><span class="sxs-lookup"><span data-stu-id="02cf3-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="02cf3-133">![Elmas bağımlılık çatışması](./media/dependencies/diamond-dependency-conflict.png "Elmas bağımlılık çatışması")</span><span class="sxs-lookup"><span data-stu-id="02cf3-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="02cf3-134">❌En az sürümü olmayan NuGet paket referansları YOKTUR.</span><span class="sxs-lookup"><span data-stu-id="02cf3-134">❌ DO NOT have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="02cf3-135">❌Kaçının NuGet paket başvuruları tam bir sürümünü talep.</span><span class="sxs-lookup"><span data-stu-id="02cf3-135">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="02cf3-136">❌Kaçının NuGet paketi referansları bir sürüm üst sınırı ile.</span><span class="sxs-lookup"><span data-stu-id="02cf3-136">❌ AVOID NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="02cf3-137">NuGet paylaşılan kaynak paketleri</span><span class="sxs-lookup"><span data-stu-id="02cf3-137">NuGet shared source packages</span></span>

<span data-ttu-id="02cf3-138">Dış NuGet paket bağımlılıklarını azaltmanın bir yolu paylaşılan kaynak paketlerine başvurmaktır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="02cf3-139">Paylaşılan kaynak paketi, başvurulduğunda projeye dahil edilen [kaynak kodu dosyalarını](/nuget/reference/nuspec#including-content-files) içerir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="02cf3-140">Projenizin geri kalanıyla derlenen kaynak kod dosyalarını dahil ettiğiniz için dışbağımlılık ve çakışma olasılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="02cf3-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="02cf3-141">Paylaşılan kaynak paketleri, küçük işlevsellik parçalarını da içeren harikadır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="02cf3-142">Örneğin, HTTP aramaları yapmak için yardımcı yöntemlerin paylaşılan bir kaynak paketi.</span><span class="sxs-lookup"><span data-stu-id="02cf3-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="02cf3-143">![Paylaşılan kaynak paketi](./media/dependencies/shared-source-package.png "Paylaşılan kaynak paketi")</span><span class="sxs-lookup"><span data-stu-id="02cf3-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="02cf3-144">![Paylaşılan kaynak projesi](./media/dependencies/shared-source-project.png "Paylaşılan kaynak projesi")</span><span class="sxs-lookup"><span data-stu-id="02cf3-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="02cf3-145">Paylaşılan kaynak paketlerinin bazı sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="02cf3-146">Bunlar `PackageReference`yalnızca, eski `packages.config` projeler hariç tutulabilir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="02cf3-147">Ayrıca paylaşılan kaynak paketleri yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="02cf3-148">Bu sınırlamalar nedeniyle paylaşılan kaynak paketleri en iyi açık kaynak proje içinde işlevselliği paylaşmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="02cf3-149">✔️ Küçük, dahili işlevsellik parçaları için paylaşılan kaynak paketlerine başvurmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="02cf3-149">✔️ CONSIDER referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="02cf3-150">✔️ Küçük, dahili işlevsellik parçaları sağlıyorsa paketinizi paylaşılan bir kaynak paketi haline getirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="02cf3-150">✔️ CONSIDER making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="02cf3-151">✔️ DO referans ile `PrivateAssets="All"`paylaşılan kaynak paketleri .</span><span class="sxs-lookup"><span data-stu-id="02cf3-151">✔️ DO reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="02cf3-152">Bu ayar, NuGet paketinin yalnızca geliştirme sırasında kullanılacağını ve genel bağımlılık olarak açıklanmaması gerektiğini söyler.</span><span class="sxs-lookup"><span data-stu-id="02cf3-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="02cf3-153">❌Ortak API'nizde paylaşılan kaynak paketi türleri YOKTUR.</span><span class="sxs-lookup"><span data-stu-id="02cf3-153">❌ DO NOT have shared source package types in your public API.</span></span>

> <span data-ttu-id="02cf3-154">Paylaşılan kaynak türleri başvuru derleme derlemesine derlenir ve derleme sınırları arasında değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="02cf3-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="02cf3-155">Örneğin, bir projedeki `IRepository` paylaşılan kaynak türü, başka bir projedeki `IRepository` aynı paylaşılan kaynaktan ayrı bir türdür.</span><span class="sxs-lookup"><span data-stu-id="02cf3-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="02cf3-156">Paylaşılan kaynak paketlerindeki türlerin `internal` görünürlüğü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02cf3-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="02cf3-157">❌Paylaşılan kaynak paketlerini NuGet.org yayınlamaYIN.</span><span class="sxs-lookup"><span data-stu-id="02cf3-157">❌ DO NOT publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="02cf3-158">Paylaşılan kaynak paketleri kaynak kodu içerir ve yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="02cf3-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="02cf3-159">Örneğin, C# paylaşılan kaynak paketi bir F# uygulaması tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="02cf3-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="02cf3-160">Paylaşılan kaynak paketlerini yerel bir [özet akışında yayımlayın veya MyGet](./publish-nuget-package.md) bunları projeniz dahilinde dahili olarak tüketin.</span><span class="sxs-lookup"><span data-stu-id="02cf3-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="02cf3-161">[Önceki](nuget.md)
>[Sonraki](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="02cf3-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>

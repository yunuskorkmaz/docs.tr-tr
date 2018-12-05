---
title: Bağımlılıklar ve .NET kitaplıkları
description: .NET kitaplıkları, NuGet bağımlılıklarını yönetmek için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 5566ab83040ce5dc23520401e3fc4bb619af4ec4
ms.sourcegitcommit: 82a3f7882bc03ed733af91fc2a0b113195bf5dc7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2018
ms.locfileid: "49400499"
---
# <a name="dependencies"></a><span data-ttu-id="f3369-103">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="f3369-103">Dependencies</span></span>

<span data-ttu-id="f3369-104">Bir .NET Kitaplığı'na bağımlılıkları ekleme birincil yolu, NuGet paketlerini başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="f3369-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="f3369-105">NuGet paket başvuruları hızlı bir şekilde yeniden kullanmak ve önceden yazılı işlevselliğinden olanak sağlar, ancak uyuşmazlıkları .NET geliştiricileri için ortak bir kaynağı oldukları.</span><span class="sxs-lookup"><span data-stu-id="f3369-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="f3369-106">Bağımlılıkları doğru şekilde yönetme, diğer .NET kitaplıkları değişiklikleri .NET Kitaplığı ' nıza kesilmesini önlemek önemlidir ve tersi!</span><span class="sxs-lookup"><span data-stu-id="f3369-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="f3369-107">Baklava bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="f3369-107">Diamond dependencies</span></span>

<span data-ttu-id="f3369-108">Bir paket birden çok sürümünü, bağımlılık ağacında bir .NET projesi için yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="f3369-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="f3369-109">Örneğin, bir uygulama her biri aynı paketin farklı sürümlerine bağlı iki NuGet paketlerini bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f3369-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="f3369-110">Uygulamanın bağımlılık grafiğinde bir baklava bağımlılık artık var.</span><span class="sxs-lookup"><span data-stu-id="f3369-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="f3369-111">![Bağımlılık elmas](./media/dependencies/diamond-dependency.png "bağımlılık elmas")</span><span class="sxs-lookup"><span data-stu-id="f3369-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="f3369-112">Oluşturma zamanında NuGet bağımlılıklarının bağımlılıklar dahil olmak üzere bir proje, bağlı olduğu tüm paketleri analiz eder.</span><span class="sxs-lookup"><span data-stu-id="f3369-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="f3369-113">Bir paket birden çok sürümünü algılandığında kurallar birini seçmek için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f3369-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="f3369-114">Aynı uygulamada bir derleme sürümlerini yan yana çalışan .NET sorunlu olduğundan paketleri birleştirme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f3369-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="f3369-115">Çoğu elmas bağımlılıkları kolayca çözümlenir; Ancak, bazı durumlarda sorunlar oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3369-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="f3369-116">**Çakışan NuGet paket başvuruları** paket geri yükleme sırasında çözümlenen bir sürüm engelle.</span><span class="sxs-lookup"><span data-stu-id="f3369-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="f3369-117">**Sürümleri arasında önemli değişiklikler** hatalar ve özel durumlar çalışma zamanında neden olur.</span><span class="sxs-lookup"><span data-stu-id="f3369-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="f3369-118">**Paket derleme tanımlayıcı ada**, derleme sürümü değişti ve uygulamanız .NET Framework üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f3369-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="f3369-119">Derleme bağlama yeniden yönlendirmeleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f3369-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="f3369-120">Paketleri ne olacağını bilmeniz mümkün değildir kendi birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3369-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="f3369-121">Kitaplığınızı bozucu bir baklava bağımlılık olasılığını azaltmak için en iyi yolu, bağımlı paketlerin sayısını en aza sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f3369-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="f3369-122">**✔️ YAPMAK** .NET kitaplığınızda gereksiz bağımlılıkları gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="f3369-122">**✔️ DO** review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="f3369-123">NuGet bağımlılık sürüm aralıklarını</span><span class="sxs-lookup"><span data-stu-id="f3369-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="f3369-124">Paket başvurusu geçerli paketleri veren aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3369-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="f3369-125">Genellikle, proje dosyasındaki paket başvurusu sürümü en düşük sürüm olan ve en büyük değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="f3369-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="f3369-126">NuGet bağımlılıkları çözümlenirken kullanan kurallar [karmaşık](/nuget/consume-packages/dependency-resolution), ancak NuGet, geçerli en düşük sürümü her zaman görünür.</span><span class="sxs-lookup"><span data-stu-id="f3369-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="f3369-127">NuGet, en yüksek kullanarak geçerli en düşük sürüm tercih ettiği en az bir uyumluluk sorunlarını en düşük olacağı için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3369-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="f3369-128">NuGet'ın en düşük uygun sürüm kural nedeniyle, bir üst sürümü veya tam aralığı en son sürümü girmeyi önlemek açısından paket başvuruları yerleştirmek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f3369-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="f3369-129">Sizin için en düşük, en uyumlu sürümü bulmak NuGet zaten çalışır.</span><span class="sxs-lookup"><span data-stu-id="f3369-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="f3369-130">Üst sürüm sınırları NuGet bir çakışma varsa başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f3369-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="f3369-131">Örneğin, bir kitaplık başka bir kitaplığı 2.0 gerekirken veya üzeri tam olarak 1.0 kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f3369-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="f3369-132">Yeni değişiklikler 2.0 sürümünde tanıtılmıştır, ancak katı veya üst sınırı sürüm bağımlılık hata garanti eder.</span><span class="sxs-lookup"><span data-stu-id="f3369-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="f3369-133">![Bağımlılık çakışma elmas](./media/dependencies/diamond-dependency-conflict.png "bağımlılık çakışma elmas")</span><span class="sxs-lookup"><span data-stu-id="f3369-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="f3369-134">**❌ SAĞLAMADIĞI** sahip NuGet paket başvuruları ile en düşük sürümü yok.</span><span class="sxs-lookup"><span data-stu-id="f3369-134">**❌ DO NOT** have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="f3369-135">**❌ KAÇININ** tam bir sürümünü gerektirdiğinden NuGet paket başvuruları.</span><span class="sxs-lookup"><span data-stu-id="f3369-135">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="f3369-136">**❌ KAÇININ** NuGet paket başvuruları sürüm üst sınırına sahip.</span><span class="sxs-lookup"><span data-stu-id="f3369-136">**❌ AVOID** NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="f3369-137">Paylaşılan NuGet kaynak paketleri</span><span class="sxs-lookup"><span data-stu-id="f3369-137">NuGet shared source packages</span></span>

<span data-ttu-id="f3369-138">Dış NuGet Paket bağımlılıklarını azaltmak için bir paylaşılan kaynak paketlerinin başvurmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="f3369-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="f3369-139">Paylaşılan kaynak pakette [kaynak kodu dosyaları](/nuget/reference/nuspec#including-content-files) başvurulduğunda bir projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="f3369-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="f3369-140">Projenizi geri kalanı ile derlenmiş kaynak kodu dosyaları yalnızca koyduğunuzdan olmadığından herhangi bir dış bağımlılık ve çakışma olasılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="f3369-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="f3369-141">Kaynak paketleri için çok küçük işlev parçalarını dahil olmak üzere paylaşılan.</span><span class="sxs-lookup"><span data-stu-id="f3369-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="f3369-142">Örneğin, bir paylaşılan kaynak paketi HTTP çağrıları yapmak için yardımcı yöntemler.</span><span class="sxs-lookup"><span data-stu-id="f3369-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="f3369-143">![Paylaşılan kaynak paketi](./media/dependencies/shared-source-package.png "paylaşılan kaynak paketi")</span><span class="sxs-lookup"><span data-stu-id="f3369-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="f3369-144">![Paylaşılan kaynak proje](./media/dependencies/shared-source-project.png "paylaşılan kaynak proje")</span><span class="sxs-lookup"><span data-stu-id="f3369-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="f3369-145">Paylaşılan kaynak paketleri bazı kısıtlamalara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f3369-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="f3369-146">Tarafından yalnızca başvurulabilir `PackageReference`, böylece eski `packages.config` projeleri hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="f3369-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="f3369-147">Ayrıca paylaşılan kaynak paketleri yalnızca aynı dil türündeki projeleri tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3369-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="f3369-148">Bu sınırlamalar nedeniyle paylaşılan kaynak paketleri en iyi şekilde işlevi bir açık kaynak projesi içinde paylaşmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3369-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="f3369-149">**✔️ DÜŞÜNÜN** paylaşılan kaynak paketleri için işlev küçük, iç parçalarını başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="f3369-149">**✔️ CONSIDER** referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="f3369-150">**✔️ DÜŞÜNÜN** işlev küçük, iç parçalarını sağlıyorsa paketinizin bir paylaşılan kaynak paketi yapma.</span><span class="sxs-lookup"><span data-stu-id="f3369-150">**✔️ CONSIDER** making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="f3369-151">**✔️ YAPMAK** paylaşılan kaynak paketlerle başvuru `PrivateAssets="All"`.</span><span class="sxs-lookup"><span data-stu-id="f3369-151">**✔️ DO** reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="f3369-152">Bu ayar, NuGet paket yalnızca geliştirme anında kullanılacak olan ve genel bir bağımlılık olarak kullanıma sunulan olmamalıdır söyler.</span><span class="sxs-lookup"><span data-stu-id="f3369-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="f3369-153">**❌ SAĞLAMADIĞI** kaynak paketi türlerinde ortak API'nizi paylaştığı.</span><span class="sxs-lookup"><span data-stu-id="f3369-153">**❌ DO NOT** have shared source package types in your public API.</span></span>

> <span data-ttu-id="f3369-154">Türleri başvuru bütünleştirilmiş kod içine derlenmiş ve bütünleştirilmiş kod sınırları arasında alınıp verilen kaynak paylaşılan.</span><span class="sxs-lookup"><span data-stu-id="f3369-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="f3369-155">Örneğin, bir paylaşılan kaynak `IRepository` türü tek bir projede, aynı paylaşılan kaynak ayrı bir türden `IRepository` başka bir projede.</span><span class="sxs-lookup"><span data-stu-id="f3369-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="f3369-156">Paylaşılan kaynak paketlerinde türler olmalıdır bir `internal` görünürlük.</span><span class="sxs-lookup"><span data-stu-id="f3369-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="f3369-157">**❌ SAĞLAMADIĞI** paylaşılan kaynak paketleri NuGet.org için yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="f3369-157">**❌ DO NOT** publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="f3369-158">Paket kaynak kodunu içeren ve yalnızca aynı dil türündeki projeleri tarafından kullanılabilir kaynak paylaşılan.</span><span class="sxs-lookup"><span data-stu-id="f3369-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="f3369-159">Örneğin, bir C# paylaşılan kaynak paketi tarafından kullanılamaz bir F# uygulama.</span><span class="sxs-lookup"><span data-stu-id="f3369-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="f3369-160">Paylaşılan kaynak paketleri yayımlama bir [yerel akış veya MyGet](./publish-nuget-package.md) bunları dahili olarak projenize içinde kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="f3369-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f3369-161">[Önceki](nuget.md)
>[İleri](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="f3369-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
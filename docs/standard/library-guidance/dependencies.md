---
title: Bağımlılıklar ve .NET kitaplıkları
description: .NET kitaplıklarında NuGet bağımlılıklarını yönetmeye yönelik en iyi yöntem önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 344d5dff564b64b9d70bbd61afb0b7bc057c8f21
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291376"
---
# <a name="dependencies"></a><span data-ttu-id="4382d-103">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="4382d-103">Dependencies</span></span>

<span data-ttu-id="4382d-104">.NET kitaplığına bağımlılık eklemenin birincil yolu NuGet paketlerine başvuruyorlardır.</span><span class="sxs-lookup"><span data-stu-id="4382d-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="4382d-105">NuGet paket başvuruları, zaten yazılmış işlevselliği hızlı bir şekilde yeniden kullanmanıza ve bu işlevselliği kullanmanıza olanak tanır, ancak .NET geliştiricileri için yaygın bir savunma kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="4382d-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="4382d-106">Bağımlılıkları doğru şekilde yönetmek, diğer .NET kitaplıklarında bulunan değişikliklerin .NET kitaplığınızı bozmasını engellemek için önemlidir, tersi de geçerlidir!</span><span class="sxs-lookup"><span data-stu-id="4382d-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="4382d-107">Elmas bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="4382d-107">Diamond dependencies</span></span>

<span data-ttu-id="4382d-108">.NET projesinin, bağımlılık ağacında bir paketin birden fazla sürümüne sahip olması yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="4382d-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="4382d-109">Örneğin, bir uygulama, her biri aynı paketin farklı sürümlerine bağlı olan iki NuGet paketine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="4382d-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="4382d-110">Bir elmas bağımlılığı artık uygulamanın bağımlılık grafiğinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4382d-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="4382d-111">![Elmas bağımlılığı](./media/dependencies/diamond-dependency.png "Elmas bağımlılığı")</span><span class="sxs-lookup"><span data-stu-id="4382d-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="4382d-112">Derleme zamanında, NuGet, bağımlılıkların bağımlılıkları da dahil olmak üzere bir projenin bağımlı olduğu tüm paketleri analiz eder.</span><span class="sxs-lookup"><span data-stu-id="4382d-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="4382d-113">Bir paketin birden çok sürümü algılandığında, kurallar bir tane seçmek üzere değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4382d-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="4382d-114">Aynı uygulamadaki bir derlemenin yan yana sürümlerini çalıştırmak .NET 'te sorunlu olduğundan paketlerin kaldırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4382d-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="4382d-115">Çoğu elmas bağımlılığı kolayca çözülür; Ancak, belirli koşullarda sorunlar oluşturabilirler:</span><span class="sxs-lookup"><span data-stu-id="4382d-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="4382d-116">**Çakışan NuGet paket başvuruları** , paketin geri yükleme sırasında bir sürümün çözümlenmesini engelliyor.</span><span class="sxs-lookup"><span data-stu-id="4382d-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="4382d-117">**Sürümler arasındaki son değişiklikler** çalışma zamanında hatalara ve özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="4382d-117">**Breaking changes between the versions** cause bugs and exceptions at run time.</span></span>
3. <span data-ttu-id="4382d-118">**Paket derlemesi tanımlayıcı adlı**, derleme sürümü değişti ve uygulama .NET Framework çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="4382d-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="4382d-119">Derleme bağlama yeniden yönlendirmeleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4382d-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="4382d-120">Hangi paketlerin sizin de birlikte kullanılacağını Bileme olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="4382d-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="4382d-121">Bir elmas bağımlılığını düşürmenin olasılığını azaltmanın iyi bir yolu, bağlı olduğunuz paket sayısını en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="4382d-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="4382d-122">✔️, .NET kitaplığınızı gereksiz bağımlılıklar için gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="4382d-122">✔️ DO review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="4382d-123">NuGet bağımlılığı sürüm aralıkları</span><span class="sxs-lookup"><span data-stu-id="4382d-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="4382d-124">Paket başvurusu, izin verdiği geçerli paketlerin aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4382d-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="4382d-125">Genellikle proje dosyasındaki paket başvuru sürümü en düşük sürümdür ve en fazla bir değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="4382d-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="4382d-126">Bir yandan,, bağımlılıkları çözümlerken NuGet tarafından kullanılan kurallar [karmaşıktır](/nuget/consume-packages/dependency-resolution), ancak [Varsayılan olarak](/nuget/consume-packages/install-use-packages-visual-studio#install-and-update-options) NuGet, en düşük uygun sürümü arar.</span><span class="sxs-lookup"><span data-stu-id="4382d-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet [by default](/nuget/consume-packages/install-use-packages-visual-studio#install-and-update-options) looks for the lowest applicable version.</span></span> <span data-ttu-id="4382d-127">En düşük uyumluluk sorunlarına sahip olacağı için NuGet, en yüksek kullanılabilir sürümü kullanarak en düşük uygun sürümü tercih eder.</span><span class="sxs-lookup"><span data-stu-id="4382d-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="4382d-128">NuGet 'in en düşük geçerli sürüm kuralı nedeniyle, en son sürümü almayı önlemek için paket başvurularına bir üst sürüm veya tam Aralık yerleştirmeniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4382d-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="4382d-129">NuGet, sizin için en düşük, en uyumlu sürümü bulmayı zaten deniyor.</span><span class="sxs-lookup"><span data-stu-id="4382d-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="4382d-130">Çakışma varsa, üst sürüm sınırları NuGet 'in başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4382d-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="4382d-131">Örneğin, bir kitaplık, farklı bir kitaplık 2,0 veya üzeri gerektirdiğinden tam olarak 1,0 kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4382d-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="4382d-132">Sürüm 2,0 ' de önemli değişiklikler sunulurken, katı veya üst sınır sürümü bağımlılığı bir hata garanti eder.</span><span class="sxs-lookup"><span data-stu-id="4382d-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="4382d-133">![Elmas bağımlılığı çakışması](./media/dependencies/diamond-dependency-conflict.png "Elmas bağımlılığı çakışması")</span><span class="sxs-lookup"><span data-stu-id="4382d-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="4382d-134">❌En düşük sürüm olmadan NuGet paketi başvuruları yoktur.</span><span class="sxs-lookup"><span data-stu-id="4382d-134">❌ DO NOT have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="4382d-135">❌Tam bir sürümü talep eden NuGet paket başvurularından KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="4382d-135">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="4382d-136">❌Sürüm üst sınırı olan NuGet paket başvurularından KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="4382d-136">❌ AVOID NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="4382d-137">NuGet paylaşılan kaynak paketleri</span><span class="sxs-lookup"><span data-stu-id="4382d-137">NuGet shared source packages</span></span>

<span data-ttu-id="4382d-138">Dış NuGet paket bağımlılıklarını azaltmanın bir yolu, paylaşılan kaynak paketlerine başvurmaktır.</span><span class="sxs-lookup"><span data-stu-id="4382d-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="4382d-139">Paylaşılan bir kaynak paketi, başvuruluyorsa bir projede yer alan [kaynak kodu dosyaları](/nuget/reference/nuspec#including-content-files) içerir.</span><span class="sxs-lookup"><span data-stu-id="4382d-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="4382d-140">Yalnızca projenizin geri kalanı ile derlenen kaynak kodu dosyalarını dahil ettiğinden, dış bağımlılık ve çakışma şansı yoktur.</span><span class="sxs-lookup"><span data-stu-id="4382d-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="4382d-141">Paylaşılan kaynak paketleri, küçük işlevsellik parçaları için harika.</span><span class="sxs-lookup"><span data-stu-id="4382d-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="4382d-142">Örneğin, HTTP çağrıları yapmak için bir yardımcı yöntem paylaşılan kaynak paketidir.</span><span class="sxs-lookup"><span data-stu-id="4382d-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="4382d-143">![Paylaşılan kaynak paketi](./media/dependencies/shared-source-package.png "Paylaşılan kaynak paketi")</span><span class="sxs-lookup"><span data-stu-id="4382d-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="4382d-144">![Paylaşılan kaynak proje](./media/dependencies/shared-source-project.png "Paylaşılan kaynak proje")</span><span class="sxs-lookup"><span data-stu-id="4382d-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="4382d-145">Paylaşılan kaynak paketlerinde bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="4382d-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="4382d-146">Yalnızca tarafından başvurulabilirler, bu `PackageReference` nedenle eski `packages.config` projeler hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="4382d-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="4382d-147">Ayrıca, paylaşılan kaynak paketleri yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4382d-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="4382d-148">Bu sınırlamalar nedeniyle, paylaşılan kaynak paketleri, bir açık kaynak proje içindeki işlevselliği paylaşmak için en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4382d-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="4382d-149">✔️ küçük, iç işlevsellik parçaları için paylaşılan kaynak paketlerine başvurmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="4382d-149">✔️ CONSIDER referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="4382d-150">✔️, küçük, iç işlevsellik parçaları sağlıyorsa paketinizi paylaşılan bir kaynak paketi yapmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="4382d-150">✔️ CONSIDER making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="4382d-151">✔️ Paylaşılan kaynak paketlerine başvuru YAPıN `PrivateAssets="All"` .</span><span class="sxs-lookup"><span data-stu-id="4382d-151">✔️ DO reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="4382d-152">Bu ayar NuGet 'e paketin yalnızca geliştirme zamanında kullanılacağını ve genel bağımlılık olarak sunulmayacağını söyler.</span><span class="sxs-lookup"><span data-stu-id="4382d-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="4382d-153">❌Ortak API 'niz içinde paylaşılan kaynak paketi türleri yok.</span><span class="sxs-lookup"><span data-stu-id="4382d-153">❌ DO NOT have shared source package types in your public API.</span></span>

> <span data-ttu-id="4382d-154">Paylaşılan kaynak türleri, başvurulan derlemeye derlenir ve derleme sınırları arasında değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4382d-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="4382d-155">Örneğin, `IRepository` bir projedeki paylaşılan kaynak türü, başka bir projede aynı paylaşılan kaynaktan ayrı bir tür `IRepository` .</span><span class="sxs-lookup"><span data-stu-id="4382d-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="4382d-156">Paylaşılan kaynak paketlerindeki türlerin görünürlüğe sahip olması gerekir `internal` .</span><span class="sxs-lookup"><span data-stu-id="4382d-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="4382d-157">❌Paylaşılan kaynak paketlerini NuGet.org 'e yayımlamayın.</span><span class="sxs-lookup"><span data-stu-id="4382d-157">❌ DO NOT publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="4382d-158">Paylaşılan kaynak paketleri kaynak kodu içerir ve yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4382d-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="4382d-159">Örneğin, bir C# paylaşılan kaynak paketi bir F # uygulaması tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4382d-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="4382d-160">Paylaşılan kaynak paketlerini yerel bir akışa yayımlayın veya bunları projenizde dahili olarak tüketmek üzere [MyGet](./publish-nuget-package.md) yapın.</span><span class="sxs-lookup"><span data-stu-id="4382d-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4382d-161">[Önceki](nuget.md) 
> [Sonraki](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="4382d-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>

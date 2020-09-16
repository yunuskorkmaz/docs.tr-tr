---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507109"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="34cef-101">Uzantılar: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="34cef-101">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="34cef-102">Bazı `Microsoft.Extensions.*` NuGet paketlerinin [DotNet/Extensions](https://github.com/dotnet/extensions) deposundan [DotNet/çalışma zamanına](https://github.com/dotnet/runtime), [ASPNET/Duyurular # 411](https://github.com/aspnet/Announcements/issues/411)' de açıklandığı gibi geçirilirken, paket değişiklikleri geçirilmiş paketlerden bazılarına uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="34cef-102">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="34cef-103">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="34cef-103">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="34cef-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="34cef-104">Version introduced</span></span>

<span data-ttu-id="34cef-105">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="34cef-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="34cef-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="34cef-106">Old behavior</span></span>

<span data-ttu-id="34cef-107">Bazı `Microsoft.Extensions.*` paketler, uygulamanızın güvenolduğu API 'ler için paket başvuruları içerir.</span><span class="sxs-lookup"><span data-stu-id="34cef-107">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="34cef-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="34cef-108">New behavior</span></span>

<span data-ttu-id="34cef-109">Uygulamanızın `Microsoft.Extensions.*` paket bağımlılıklarını eklemesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="34cef-109">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="34cef-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="34cef-110">Reason for change</span></span>

<span data-ttu-id="34cef-111">Paketleme ilkeleri *DotNet/Runtime* deposuna daha iyi uyum sağlamak için güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="34cef-111">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="34cef-112">Yeni ilke altında kullanılmayan paket başvuruları paketleme sırasında *. nupkg* dosyalarından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="34cef-112">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="34cef-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="34cef-113">Recommended action</span></span>

<span data-ttu-id="34cef-114">Etkilenen paketlerin tüketicileri, kaldırılan paket bağımlılığıyla API 'Ler kullanılırsa, bu projedeki kaldırılan paket bağımlılığına doğrudan bağımlılık eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="34cef-114">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="34cef-115">Aşağıdaki tabloda etkilenen paketler ve ilgili değişiklikler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="34cef-115">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="34cef-116">Paket adı</span><span class="sxs-lookup"><span data-stu-id="34cef-116">Package name</span></span>|<span data-ttu-id="34cef-117">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="34cef-117">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="34cef-118">Microsoft.Extensions.Configurlama. Bağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="34cef-118">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="34cef-119">Başvurusu kaldırıldı `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="34cef-119">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="34cef-120"> ÜzerindeMicrosoft.Extensions.Configuration.Js</span><span class="sxs-lookup"><span data-stu-id="34cef-120">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="34cef-121">Başvurusu kaldırıldı `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="34cef-121">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="34cef-122">Microsoft. Extensions. Hosting. soyutlamalar</span><span class="sxs-lookup"><span data-stu-id="34cef-122">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="34cef-123">Başvurusu kaldırıldı `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="34cef-123">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="34cef-124">Microsoft. Extensions. Logging</span><span class="sxs-lookup"><span data-stu-id="34cef-124">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="34cef-125">Başvurusu kaldırıldı `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="34cef-125">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="34cef-126">Microsoft. Extensions. Logging. Console</span><span class="sxs-lookup"><span data-stu-id="34cef-126">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="34cef-127">Başvurusu kaldırıldı `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="34cef-127">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="34cef-128">Microsoft. Extensions. Logging. EventLog</span><span class="sxs-lookup"><span data-stu-id="34cef-128">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="34cef-129">`System.Diagnostics.EventLog`.NET Framework 4.6.1 hedef Framework bilinen adı için başvuru kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="34cef-129">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="34cef-130">Microsoft. Extensions. Logging. EventSource</span><span class="sxs-lookup"><span data-stu-id="34cef-130">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="34cef-131">Başvurusu kaldırıldı `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="34cef-131">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="34cef-132">Microsoft. Extensions. Options</span><span class="sxs-lookup"><span data-stu-id="34cef-132">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="34cef-133">Başvurusu kaldırıldı `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="34cef-133">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="34cef-134">Örneğin, öğesine paket başvurusu `Microsoft.Extensions.Configuration` öğesinden kaldırılmıştır `Microsoft.Extensions.Configuration.Binder` .</span><span class="sxs-lookup"><span data-stu-id="34cef-134">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="34cef-135">Pakette, bağımlılıktan API kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="34cef-135">No API from the dependency was used in the package.</span></span> <span data-ttu-id="34cef-136">`Microsoft.Extensions.Configuration.Binder`API 'lerine bağlı olan kullanıcıların `Microsoft.Extensions.Configuration` , projesinde kendisine bir doğrudan başvuru eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="34cef-136">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

#### <a name="category"></a><span data-ttu-id="34cef-137">Kategori</span><span class="sxs-lookup"><span data-stu-id="34cef-137">Category</span></span>

<span data-ttu-id="34cef-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="34cef-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="34cef-139">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="34cef-139">Affected APIs</span></span>

<span data-ttu-id="34cef-140">Yok</span><span class="sxs-lookup"><span data-stu-id="34cef-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

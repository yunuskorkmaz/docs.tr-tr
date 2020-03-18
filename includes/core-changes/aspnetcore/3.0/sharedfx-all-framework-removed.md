---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394434"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="83117-101">Paylaşılan çerçeve: Kaldırıldı Microsoft.AspNetCore.All</span><span class="sxs-lookup"><span data-stu-id="83117-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="83117-102">Core 3.0ASP.NETdan `Microsoft.AspNetCore.All` başlayarak, metapaket `Microsoft.AspNetCore.All` ve eşleşen paylaşılan çerçeve artık üretilmemaktadır.</span><span class="sxs-lookup"><span data-stu-id="83117-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="83117-103">Bu paket Core 2.2ASP.NETde mevcuttur ve ASP.NET Core 2.1'de servis güncellemeleri almaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="83117-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83117-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="83117-104">Version introduced</span></span>

<span data-ttu-id="83117-105">3,0</span><span class="sxs-lookup"><span data-stu-id="83117-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="83117-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="83117-106">Old behavior</span></span>

<span data-ttu-id="83117-107">`Microsoft.AspNetCore.All` Uygulamalar,.NET Core'daki `Microsoft.AspNetCore.All` paylaşılan çerçeveyi hedeflemek için meta paketi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="83117-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="83117-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="83117-108">New behavior</span></span>

<span data-ttu-id="83117-109">.NET Core 3.0 paylaşılan `Microsoft.AspNetCore.All` bir çerçeve içermez.</span><span class="sxs-lookup"><span data-stu-id="83117-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="83117-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="83117-110">Reason for change</span></span>

<span data-ttu-id="83117-111">Meta `Microsoft.AspNetCore.All` paket çok sayıda dış bağımlılık içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="83117-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83117-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="83117-112">Recommended action</span></span>

<span data-ttu-id="83117-113">Çerçeveyi kullanmak için `Microsoft.AspNetCore.App` projenizi geçirin.</span><span class="sxs-lookup"><span data-stu-id="83117-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="83117-114">Daha önce mevcut olan `Microsoft.AspNetCore.All` bileşenler NuGet'de hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83117-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="83117-115">Bu bileşenler artık paylaşılan çerçeveye dahil olmak yerine uygulamanızla birlikte dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="83117-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="83117-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="83117-116">Category</span></span>

<span data-ttu-id="83117-117">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="83117-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83117-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="83117-118">Affected APIs</span></span>

<span data-ttu-id="83117-119">None</span><span class="sxs-lookup"><span data-stu-id="83117-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

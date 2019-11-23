---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394434"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="3a9fa-101">Paylaşılan çerçeve: Microsoft. AspNetCore. All kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="3a9fa-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="3a9fa-102">ASP.NET Core 3,0 ' den başlayarak, `Microsoft.AspNetCore.All` metapackage ve eşleşen `Microsoft.AspNetCore.All` paylaşılan Framework artık üretilmez.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="3a9fa-103">Bu paket ASP.NET Core 2,2 ' de kullanılabilir ve ASP.NET Core 2,1 ' de hizmet güncelleştirmelerini almaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a9fa-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3a9fa-104">Version introduced</span></span>

<span data-ttu-id="3a9fa-105">3,0</span><span class="sxs-lookup"><span data-stu-id="3a9fa-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3a9fa-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3a9fa-106">Old behavior</span></span>

<span data-ttu-id="3a9fa-107">Uygulamalar, .NET Core 'da `Microsoft.AspNetCore.All` paylaşılan Framework 'ü hedeflemek için `Microsoft.AspNetCore.All` metapaketini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3a9fa-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3a9fa-108">New behavior</span></span>

<span data-ttu-id="3a9fa-109">.NET Core 3,0 `Microsoft.AspNetCore.All` paylaşılan bir çerçeve içermez.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3a9fa-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3a9fa-110">Reason for change</span></span>

<span data-ttu-id="3a9fa-111">`Microsoft.AspNetCore.All` metapackage çok sayıda dış bağımlılığı içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a9fa-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3a9fa-112">Recommended action</span></span>

<span data-ttu-id="3a9fa-113">`Microsoft.AspNetCore.App` çerçevesini kullanmak için projenizi geçirin.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="3a9fa-114">Daha önce `Microsoft.AspNetCore.All` ' de kullanılabilir olan bileşenler NuGet üzerinde hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="3a9fa-115">Bu bileşenler artık, paylaşılan çerçeveye eklenmek yerine uygulamanızla birlikte dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="3a9fa-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="3a9fa-116">Category</span></span>

<span data-ttu-id="3a9fa-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3a9fa-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a9fa-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3a9fa-118">Affected APIs</span></span>

<span data-ttu-id="3a9fa-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a9fa-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

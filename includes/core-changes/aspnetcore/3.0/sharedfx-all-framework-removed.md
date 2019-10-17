---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394434"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="3649c-101">Paylaşılan çerçeve: Microsoft. AspNetCore. All kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="3649c-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="3649c-102">ASP.NET Core 3,0 ' den başlayarak, `Microsoft.AspNetCore.All` metapackage ve eşleşen `Microsoft.AspNetCore.All` Paylaşılan Framework artık üretilmez.</span><span class="sxs-lookup"><span data-stu-id="3649c-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="3649c-103">Bu paket ASP.NET Core 2,2 ' de kullanılabilir ve ASP.NET Core 2,1 ' de hizmet güncelleştirmelerini almaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="3649c-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3649c-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3649c-104">Version introduced</span></span>

<span data-ttu-id="3649c-105">3.0</span><span class="sxs-lookup"><span data-stu-id="3649c-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3649c-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3649c-106">Old behavior</span></span>

<span data-ttu-id="3649c-107">Uygulamalar, .NET Core 'da `Microsoft.AspNetCore.All` Paylaşılan çerçevesini hedeflemek için `Microsoft.AspNetCore.All` metapaketini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3649c-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3649c-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3649c-108">New behavior</span></span>

<span data-ttu-id="3649c-109">.NET Core 3,0 @no__t 0 paylaşılan bir çerçeve içermez.</span><span class="sxs-lookup"><span data-stu-id="3649c-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3649c-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3649c-110">Reason for change</span></span>

<span data-ttu-id="3649c-111">@No__t-0 metapackage çok sayıda dış bağımlılığı içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="3649c-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3649c-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3649c-112">Recommended action</span></span>

<span data-ttu-id="3649c-113">@No__t-0 çerçevesini kullanmak için projenizi geçirin.</span><span class="sxs-lookup"><span data-stu-id="3649c-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="3649c-114">@No__t-0 ' da daha önce kullanılabilir olan bileşenler NuGet üzerinde hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3649c-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="3649c-115">Bu bileşenler artık, paylaşılan çerçeveye eklenmek yerine uygulamanızla birlikte dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="3649c-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="3649c-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="3649c-116">Category</span></span>

<span data-ttu-id="3649c-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3649c-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3649c-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3649c-118">Affected APIs</span></span>

<span data-ttu-id="3649c-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="3649c-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

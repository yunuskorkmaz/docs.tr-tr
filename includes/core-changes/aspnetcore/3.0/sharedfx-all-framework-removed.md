---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032862"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="40457-101">Paylaşılan çerçeve: Microsoft. AspNetCore. All kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="40457-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="40457-102">ASP.NET Core 3,0 ' den başlayarak, `Microsoft.AspNetCore.All` metapackage ve eşleşen `Microsoft.AspNetCore.All` paylaşılan çerçeve artık üretilmez.</span><span class="sxs-lookup"><span data-stu-id="40457-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="40457-103">Bu paket ASP.NET Core 2,2 ' de kullanılabilir ve ASP.NET Core 2,1 ' de hizmet güncelleştirmelerini almaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="40457-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40457-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="40457-104">Version introduced</span></span>

<span data-ttu-id="40457-105">3,0</span><span class="sxs-lookup"><span data-stu-id="40457-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="40457-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="40457-106">Old behavior</span></span>

<span data-ttu-id="40457-107">Uygulamalar, `Microsoft.AspNetCore.All` `Microsoft.AspNetCore.All` .NET Core 'da paylaşılan çerçeveyi hedeflemek için metapackage kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="40457-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="40457-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="40457-108">New behavior</span></span>

<span data-ttu-id="40457-109">.NET Core 3,0, paylaşılan bir `Microsoft.AspNetCore.All` çerçeve içermez.</span><span class="sxs-lookup"><span data-stu-id="40457-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="40457-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="40457-110">Reason for change</span></span>

<span data-ttu-id="40457-111">`Microsoft.AspNetCore.All`Metapackage çok sayıda dış bağımlılığı içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="40457-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40457-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="40457-112">Recommended action</span></span>

<span data-ttu-id="40457-113">Çerçevesini kullanmak için projenizi geçirin `Microsoft.AspNetCore.App` .</span><span class="sxs-lookup"><span data-stu-id="40457-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="40457-114">Daha önce ' de kullanılabilir olan bileşenler `Microsoft.AspNetCore.All` NuGet üzerinde hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40457-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="40457-115">Bu bileşenler artık, paylaşılan çerçeveye eklenmek yerine uygulamanızla birlikte dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="40457-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="40457-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="40457-116">Category</span></span>

<span data-ttu-id="40457-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40457-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40457-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="40457-118">Affected APIs</span></span>

<span data-ttu-id="40457-119">Yok</span><span class="sxs-lookup"><span data-stu-id="40457-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

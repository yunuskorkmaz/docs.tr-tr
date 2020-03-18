---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198593"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="1d862-101">Önbelleğe alma: Microsoft.Extensions.Caching.SqlServer yeni SqlClient paketi kullanır</span><span class="sxs-lookup"><span data-stu-id="1d862-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="1d862-102">Paket, `Microsoft.Extensions.Caching.SqlServer` `System.Data.SqlClient` paket yerine `Microsoft.Data.SqlClient` yeni paketi kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d862-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="1d862-103">Bu değişiklik hafif davranışsal kırılma değişikliklerine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d862-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="1d862-104">Daha fazla bilgi için [bkz.](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)</span><span class="sxs-lookup"><span data-stu-id="1d862-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1d862-105">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="1d862-105">Version introduced</span></span>

<span data-ttu-id="1d862-106">3,0</span><span class="sxs-lookup"><span data-stu-id="1d862-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1d862-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="1d862-107">Old behavior</span></span>

<span data-ttu-id="1d862-108">Paket `Microsoft.Extensions.Caching.SqlServer` `System.Data.SqlClient` paketi kullandı.</span><span class="sxs-lookup"><span data-stu-id="1d862-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1d862-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="1d862-109">New behavior</span></span>

<span data-ttu-id="1d862-110">`Microsoft.Extensions.Caching.SqlServer`şimdi `Microsoft.Data.SqlClient` paketi kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="1d862-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1d862-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="1d862-111">Reason for change</span></span>

<span data-ttu-id="1d862-112">`Microsoft.Data.SqlClient`kapalı inşa edilmiş yeni bir `System.Data.SqlClient`pakettir.</span><span class="sxs-lookup"><span data-stu-id="1d862-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="1d862-113">Bundan sonra tüm yeni özellik çalışmaları burada yapılacak.</span><span class="sxs-lookup"><span data-stu-id="1d862-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1d862-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1d862-114">Recommended action</span></span>

<span data-ttu-id="1d862-115">`Microsoft.Extensions.Caching.SqlServer` Müşteriler, paket tarafından döndürülen türleri kullanmadıkları ve bunları türe dönüştürmedikleri `System.Data.SqlClient` sürece bu kırılma değişikliği hakkında endişelenmelerine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d862-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="1d862-116">Örneğin, birisi [eski SqlConnection türüne](xref:System.Data.SqlClient.SqlConnection)a `DbConnection` atıyorduysa, kalıbı `Microsoft.Data.SqlClient.SqlConnection` yeni türe değiştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d862-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="1d862-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="1d862-117">Category</span></span>

<span data-ttu-id="1d862-118">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="1d862-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1d862-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1d862-119">Affected APIs</span></span>

<span data-ttu-id="1d862-120">None</span><span class="sxs-lookup"><span data-stu-id="1d862-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

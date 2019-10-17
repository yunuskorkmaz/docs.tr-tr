---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393912"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="aa24a-101">Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır</span><span class="sxs-lookup"><span data-stu-id="aa24a-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="aa24a-102">@No__t-0 paketi `System.Data.SqlClient` paketi yerine yeni `Microsoft.Data.SqlClient` paketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa24a-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="aa24a-103">Bu değişiklik küçük davranışsal davranış değişikliklerine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="aa24a-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="aa24a-104">Daha fazla bilgi için bkz. [Yeni Microsoft. Data. SqlClient tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="aa24a-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aa24a-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="aa24a-105">Version introduced</span></span>

<span data-ttu-id="aa24a-106">3.0</span><span class="sxs-lookup"><span data-stu-id="aa24a-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="aa24a-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="aa24a-107">Old behavior</span></span>

<span data-ttu-id="aa24a-108">@No__t-0 paketi `System.Data.SqlClient` paketini kullandı.</span><span class="sxs-lookup"><span data-stu-id="aa24a-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="aa24a-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="aa24a-109">New behavior</span></span>

<span data-ttu-id="aa24a-110">`Microsoft.Extensions.Caching.SqlServer` artık `Microsoft.Data.SqlClient` paketini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="aa24a-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="aa24a-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="aa24a-111">Reason for change</span></span>

<span data-ttu-id="aa24a-112">`Microsoft.Data.SqlClient`, `System.Data.SqlClient` ' den oluşturulan yeni bir pakettir.</span><span class="sxs-lookup"><span data-stu-id="aa24a-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="aa24a-113">Bu, tüm yeni özellik işinin bundan sonra yapıldığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="aa24a-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aa24a-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="aa24a-114">Recommended action</span></span>

<span data-ttu-id="aa24a-115">@No__t-0 paketi tarafından döndürülen türleri kullanmadıkları ve bunları `System.Data.SqlClient` türlerine aktarmadığı müddetçe müşterilerin bu son değişiklik hakkında endişelenmeleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="aa24a-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="aa24a-116">Örneğin, birisi `DbConnection` ' ı [eski SqlConnection türüne](xref:System.Data.SqlClient.SqlConnection)alıyorsa, yeni @no__t 2 türüne dönüştürmeyi değiştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa24a-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span> 

#### <a name="category"></a><span data-ttu-id="aa24a-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="aa24a-117">Category</span></span>

<span data-ttu-id="aa24a-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aa24a-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aa24a-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="aa24a-119">Affected APIs</span></span>

<span data-ttu-id="aa24a-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa24a-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

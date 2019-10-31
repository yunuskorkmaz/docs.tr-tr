---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198593"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="a03a7-101">Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır</span><span class="sxs-lookup"><span data-stu-id="a03a7-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="a03a7-102">`Microsoft.Extensions.Caching.SqlServer` paketi `System.Data.SqlClient` paketi yerine yeni `Microsoft.Data.SqlClient` paketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a03a7-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="a03a7-103">Bu değişiklik küçük davranışsal davranış değişikliklerine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a03a7-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="a03a7-104">Daha fazla bilgi için bkz. [Yeni Microsoft. Data. SqlClient tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="a03a7-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a03a7-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a03a7-105">Version introduced</span></span>

<span data-ttu-id="a03a7-106">3.0</span><span class="sxs-lookup"><span data-stu-id="a03a7-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a03a7-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a03a7-107">Old behavior</span></span>

<span data-ttu-id="a03a7-108">`Microsoft.Extensions.Caching.SqlServer` paketi `System.Data.SqlClient` paketini kullandı.</span><span class="sxs-lookup"><span data-stu-id="a03a7-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a03a7-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a03a7-109">New behavior</span></span>

<span data-ttu-id="a03a7-110">`Microsoft.Extensions.Caching.SqlServer` artık `Microsoft.Data.SqlClient` paketini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="a03a7-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a03a7-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a03a7-111">Reason for change</span></span>

<span data-ttu-id="a03a7-112">`Microsoft.Data.SqlClient`, `System.Data.SqlClient` ' den oluşturulan yeni bir pakettir.</span><span class="sxs-lookup"><span data-stu-id="a03a7-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="a03a7-113">Bu, tüm yeni özellik işinin bundan sonra yapıldığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="a03a7-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a03a7-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a03a7-114">Recommended action</span></span>

<span data-ttu-id="a03a7-115">Müşterilerin, `Microsoft.Extensions.Caching.SqlServer` paketi tarafından döndürülen türleri kullanmadıkları ve bunları `System.Data.SqlClient` türlerine dönüştürmedikleri müddetçe, bu son değişiklik hakkında kaygılanmaması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a03a7-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="a03a7-116">Örneğin, birisi [eski SqlConnection türüne](xref:System.Data.SqlClient.SqlConnection)bir `DbConnection` dönüştürrsa, yeni `Microsoft.Data.SqlClient.SqlConnection` türüne dönüştürmeyi değiştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a03a7-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="a03a7-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="a03a7-117">Category</span></span>

<span data-ttu-id="a03a7-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a03a7-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a03a7-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a03a7-119">Affected APIs</span></span>

<span data-ttu-id="a03a7-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="a03a7-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

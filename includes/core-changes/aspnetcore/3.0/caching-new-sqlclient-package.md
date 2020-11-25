---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032724"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="7f981-101">Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır</span><span class="sxs-lookup"><span data-stu-id="7f981-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="7f981-102">`Microsoft.Extensions.Caching.SqlServer`Paket, `Microsoft.Data.SqlClient` paket yerine yeni paketini kullanır `System.Data.SqlClient` .</span><span class="sxs-lookup"><span data-stu-id="7f981-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="7f981-103">Bu değişiklik küçük davranışsal davranış değişikliklerine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f981-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="7f981-104">Daha fazla bilgi için bkz. [Yeni Microsoft. Data. SqlClient tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="7f981-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7f981-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7f981-105">Version introduced</span></span>

<span data-ttu-id="7f981-106">3,0</span><span class="sxs-lookup"><span data-stu-id="7f981-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7f981-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="7f981-107">Old behavior</span></span>

<span data-ttu-id="7f981-108">`Microsoft.Extensions.Caching.SqlServer`Paket, paketi kullandı `System.Data.SqlClient` .</span><span class="sxs-lookup"><span data-stu-id="7f981-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7f981-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="7f981-109">New behavior</span></span>

<span data-ttu-id="7f981-110">`Microsoft.Extensions.Caching.SqlServer` Artık `Microsoft.Data.SqlClient` paketi kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="7f981-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7f981-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7f981-111">Reason for change</span></span>

<span data-ttu-id="7f981-112">`Microsoft.Data.SqlClient` , ' den oluşturulan yeni bir pakettir `System.Data.SqlClient` .</span><span class="sxs-lookup"><span data-stu-id="7f981-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="7f981-113">Bu, tüm yeni özellik işinin bundan sonra yapıldığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="7f981-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7f981-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7f981-114">Recommended action</span></span>

<span data-ttu-id="7f981-115">Müşterilerin, paket tarafından döndürülen türleri kullanmadıkları `Microsoft.Extensions.Caching.SqlServer` ve bunları türlere dönüştürmedikleri müddetçe, bu son değişiklik konusunda endişelenmeleri gerekmez `System.Data.SqlClient` .</span><span class="sxs-lookup"><span data-stu-id="7f981-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="7f981-116">Örneğin, birisi, `DbConnection` [eski SqlConnection türünde](xref:System.Data.SqlClient.SqlConnection)bir olarak yayınlandıysa, dönüştürmeyi yeni türe dönüştürmeleri gerekir `Microsoft.Data.SqlClient.SqlConnection` .</span><span class="sxs-lookup"><span data-stu-id="7f981-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="7f981-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="7f981-117">Category</span></span>

<span data-ttu-id="7f981-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7f981-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7f981-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7f981-119">Affected APIs</span></span>

<span data-ttu-id="7f981-120">Yok</span><span class="sxs-lookup"><span data-stu-id="7f981-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

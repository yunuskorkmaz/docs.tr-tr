---
ms.openlocfilehash: 8c593fa6490451c6236f0d4390f09d4e9e4f0cbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497080"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a><span data-ttu-id="34a16-101">ObjectContext. CreateDatabase ve DbProviderServices. CreateDatabase metotları için farklı özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="34a16-101">Different exception handling for ObjectContext.CreateDatabase and DbProviderServices.CreateDatabase methods</span></span>

#### <a name="details"></a><span data-ttu-id="34a16-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="34a16-102">Details</span></span>

<span data-ttu-id="34a16-103">.NET Framework 4,5 ' den başlayarak, veritabanı oluşturma başarısız olursa, <code>CreateDatabase</code> Yöntemler boş veritabanını bırakmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="34a16-103">Beginning in .NET Framework 4.5, if database creation fails, <code>CreateDatabase</code> methods will attempt to drop the empty database.</span></span> <span data-ttu-id="34a16-104">Bu işlem başarılı olursa, orijinalin <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> yayılacağı ( <xref:System.InvalidOperationException?displayProperty=fullName> .NET Framework 4,0 ' de her zaman oluşturulan)</span><span class="sxs-lookup"><span data-stu-id="34a16-104">If that operation succeeds, the original <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> will be propagated (instead of the <xref:System.InvalidOperationException?displayProperty=fullName> that was always thrown in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="34a16-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="34a16-105">Suggestion</span></span>

<span data-ttu-id="34a16-106"><xref:System.InvalidOperationException?displayProperty=fullName>Ya da yürütülürken <xref:System.Data.Objects.ObjectContext.CreateDatabase> veya <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> SqlExceptions artık yakalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34a16-106">When catching an <xref:System.InvalidOperationException?displayProperty=fullName> while executing <xref:System.Data.Objects.ObjectContext.CreateDatabase> or <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions should now also be caught.</span></span>

| <span data-ttu-id="34a16-107">Name</span><span class="sxs-lookup"><span data-stu-id="34a16-107">Name</span></span>    | <span data-ttu-id="34a16-108">Değer</span><span class="sxs-lookup"><span data-stu-id="34a16-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="34a16-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="34a16-109">Scope</span></span>   |<span data-ttu-id="34a16-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="34a16-110">Minor</span></span>|
|<span data-ttu-id="34a16-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="34a16-111">Version</span></span>|<span data-ttu-id="34a16-112">4,5</span><span class="sxs-lookup"><span data-stu-id="34a16-112">4.5</span></span>|
|<span data-ttu-id="34a16-113">Tür</span><span class="sxs-lookup"><span data-stu-id="34a16-113">Type</span></span>|<span data-ttu-id="34a16-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="34a16-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="34a16-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="34a16-115">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>
- <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`
- `M:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)`

-->

---
ms.openlocfilehash: 81992e57d7e92b4df92ce68870c0272d6cd5b220
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496153"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="49405-101">ObjectContext. Translate ve ObjectContext.ExecuteStoreQuery artık sabit listesi türünü destekliyor</span><span class="sxs-lookup"><span data-stu-id="49405-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="49405-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="49405-102">Details</span></span>

<span data-ttu-id="49405-103">.NET Framework 4,0 ' de, <code>T</code> <code>ObjectContext.Translate</code> ve yöntemlerinin genel parametresi <code>ObjectContext.ExecuteStoreQuery</code> bir sabit listesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="49405-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="49405-104">Bu senaryo artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="49405-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="49405-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="49405-105">Suggestion</span></span>

<span data-ttu-id="49405-106">.NET Framework 4,0 ' de bir sabit listesi türü üzerinde çevir veya ExecuteStoreQuery çağrılırsa, ' 0 ' döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="49405-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="49405-107">Bu davranış istenirse, çağrılar bir sabit 0 (veya Enum ile eşdeğer) ile değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="49405-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="49405-108">Name</span><span class="sxs-lookup"><span data-stu-id="49405-108">Name</span></span>    | <span data-ttu-id="49405-109">Değer</span><span class="sxs-lookup"><span data-stu-id="49405-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="49405-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="49405-110">Scope</span></span>   |<span data-ttu-id="49405-111">Edge</span><span class="sxs-lookup"><span data-stu-id="49405-111">Edge</span></span>|
|<span data-ttu-id="49405-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="49405-112">Version</span></span>|<span data-ttu-id="49405-113">4,5</span><span class="sxs-lookup"><span data-stu-id="49405-113">4.5</span></span>|
|<span data-ttu-id="49405-114">Tür</span><span class="sxs-lookup"><span data-stu-id="49405-114">Type</span></span>|<span data-ttu-id="49405-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="49405-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="49405-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="49405-116">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

<!--

#### Affected APIs

- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader)``
- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.Object[])``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])``

-->

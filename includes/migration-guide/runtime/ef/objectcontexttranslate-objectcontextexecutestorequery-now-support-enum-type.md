---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620628"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="b5222-101">ObjectContext. Translate ve ObjectContext.ExecuteStoreQuery artık sabit listesi türünü destekliyor</span><span class="sxs-lookup"><span data-stu-id="b5222-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="b5222-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b5222-102">Details</span></span>

<span data-ttu-id="b5222-103">.NET Framework 4,0 ' de, <code>T</code> <code>ObjectContext.Translate</code> ve yöntemlerinin genel parametresi <code>ObjectContext.ExecuteStoreQuery</code> bir sabit listesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="b5222-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="b5222-104">Bu senaryo artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b5222-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b5222-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b5222-105">Suggestion</span></span>

<span data-ttu-id="b5222-106">.NET Framework 4,0 ' de bir sabit listesi türü üzerinde çevir veya ExecuteStoreQuery çağrılırsa, ' 0 ' döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b5222-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="b5222-107">Bu davranış istenirse, çağrılar bir sabit 0 (veya Enum ile eşdeğer) ile değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b5222-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="b5222-108">Name</span><span class="sxs-lookup"><span data-stu-id="b5222-108">Name</span></span>    | <span data-ttu-id="b5222-109">Değer</span><span class="sxs-lookup"><span data-stu-id="b5222-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b5222-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b5222-110">Scope</span></span>   |<span data-ttu-id="b5222-111">Edge</span><span class="sxs-lookup"><span data-stu-id="b5222-111">Edge</span></span>|
|<span data-ttu-id="b5222-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b5222-112">Version</span></span>|<span data-ttu-id="b5222-113">4,5</span><span class="sxs-lookup"><span data-stu-id="b5222-113">4.5</span></span>|
|<span data-ttu-id="b5222-114">Tür</span><span class="sxs-lookup"><span data-stu-id="b5222-114">Type</span></span>|<span data-ttu-id="b5222-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b5222-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b5222-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b5222-116">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

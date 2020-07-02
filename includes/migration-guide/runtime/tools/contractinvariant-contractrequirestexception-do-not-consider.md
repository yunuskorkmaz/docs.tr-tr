---
ms.openlocfilehash: 29c66edfeb1690199aac39b9c3076d161b2075d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621441"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="b80b1-101">Contract. sabit veya sözleşme. \<TException> Için String. IsNullOrEmpty 'ın saf olmasını gerektirmeyin</span><span class="sxs-lookup"><span data-stu-id="b80b1-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="b80b1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b80b1-102">Details</span></span>

<span data-ttu-id="b80b1-103">.NET Framework 4.6.1 ' i hedefleyen uygulamalar için, <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> veya önkoşul sözleşmesi için olan sabit sözleşme <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> yöntemini çağırırsa, Rewriter derleyicinin uyarı CC1036: &quot; ' System. String. ısnullorwhtespace (System. String) ' metoduna [saf] olmadan çağrı algıladı. &quot; Bu, derleyici hatası yerine bir derleyici uyarısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b80b1-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b80b1-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="b80b1-104">Suggestion</span></span>

<span data-ttu-id="b80b1-105">Bu davranış, [GitHub sorun #339](https://github.com/Microsoft/CodeContracts/issues/339)' de giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b80b1-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="b80b1-106">Bu uyarıyı ortadan kaldırmak için, [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md)'Dan kod sözleşmeleri aracı için kaynak kodun güncelleştirilmiş bir sürümünü indirebilir ve derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b80b1-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="b80b1-107">İndirme bilgileri sayfanın alt kısmında bulunur.</span><span class="sxs-lookup"><span data-stu-id="b80b1-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="b80b1-108">Name</span><span class="sxs-lookup"><span data-stu-id="b80b1-108">Name</span></span>    | <span data-ttu-id="b80b1-109">Değer</span><span class="sxs-lookup"><span data-stu-id="b80b1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b80b1-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b80b1-110">Scope</span></span>   |<span data-ttu-id="b80b1-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="b80b1-111">Minor</span></span>|
|<span data-ttu-id="b80b1-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b80b1-112">Version</span></span>|<span data-ttu-id="b80b1-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="b80b1-113">4.6.1</span></span>|
|<span data-ttu-id="b80b1-114">Tür</span><span class="sxs-lookup"><span data-stu-id="b80b1-114">Type</span></span>|<span data-ttu-id="b80b1-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b80b1-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b80b1-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b80b1-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

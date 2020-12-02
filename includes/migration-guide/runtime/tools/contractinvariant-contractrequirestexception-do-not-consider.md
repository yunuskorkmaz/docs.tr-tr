---
ms.openlocfilehash: 639cd13978cc33bd7c4524a17e92d566404bbaea
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477644"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="5cedc-101">Contract. sabit veya sözleşme. \<TException> Için String. IsNullOrEmpty 'ın saf olmasını gerektirmeyin</span><span class="sxs-lookup"><span data-stu-id="5cedc-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="5cedc-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5cedc-102">Details</span></span>

<span data-ttu-id="5cedc-103">.NET Framework 4.6.1 ' i hedefleyen uygulamalar için, <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> veya önkoşul sözleşmesi için olan sabit sözleşme, <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> yöntemi çağırırsa, Rewriter derleyici uyarısı CC1036: &quot; ' System. String. IsNullOrWhiteSpace (System. String) ' metoduna [saf] yöntemi olmadan çağrı algıladı. &quot; Bu, derleyici hatası yerine bir derleyici uyarısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5cedc-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhiteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5cedc-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="5cedc-104">Suggestion</span></span>

<span data-ttu-id="5cedc-105">Bu davranış, [GitHub sorun #339](https://github.com/Microsoft/CodeContracts/issues/339)' de giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5cedc-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="5cedc-106">Bu uyarıyı ortadan kaldırmak için, [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md)'Dan kod sözleşmeleri aracı için kaynak kodun güncelleştirilmiş bir sürümünü indirebilir ve derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cedc-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="5cedc-107">İndirme bilgileri sayfanın alt kısmında bulunur.</span><span class="sxs-lookup"><span data-stu-id="5cedc-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="5cedc-108">Ad</span><span class="sxs-lookup"><span data-stu-id="5cedc-108">Name</span></span>    | <span data-ttu-id="5cedc-109">Değer</span><span class="sxs-lookup"><span data-stu-id="5cedc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5cedc-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5cedc-110">Scope</span></span>   |<span data-ttu-id="5cedc-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="5cedc-111">Minor</span></span>|
|<span data-ttu-id="5cedc-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5cedc-112">Version</span></span>|<span data-ttu-id="5cedc-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="5cedc-113">4.6.1</span></span>|
|<span data-ttu-id="5cedc-114">Tür</span><span class="sxs-lookup"><span data-stu-id="5cedc-114">Type</span></span>|<span data-ttu-id="5cedc-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5cedc-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5cedc-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5cedc-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->

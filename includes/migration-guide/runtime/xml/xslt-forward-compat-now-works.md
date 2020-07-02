---
ms.openlocfilehash: e3b9711ac66901d69838de4c9f309d086b06fd4d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620730"
---
### <a name="xslt-forward-compat-now-works"></a><span data-ttu-id="6d25c-101">XSLT ileriye dönük uyumluluk artık çalışmaktadır</span><span class="sxs-lookup"><span data-stu-id="6d25c-101">XSLT forward compat now works</span></span>

#### <a name="details"></a><span data-ttu-id="6d25c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6d25c-102">Details</span></span>

<span data-ttu-id="6d25c-103">.NET Framework 4 ' te, XSLT 1,0 ileri uyumluluğu aşağıdaki sorunlara sahipti:</span><span class="sxs-lookup"><span data-stu-id="6d25c-103">In the .NET Framework 4, XSLT 1.0 forward compatibility had the following issues:</span></span><ul><li><span data-ttu-id="6d25c-104">Sürümü 2.0 değerine ayarlanmış bir stil sayfasının yüklenmesi başarısız oldu ve ayrıştırıcı tanınmayan bir XSLT 1.0 yapısıyla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="6d25c-104">Loading a style sheet failed if its version was set to 2.0 and the parser encountered an unrecognized XSLT 1.0 construct.</span></span></li><li><span data-ttu-id="6d25c-105"><code>xsl:sort</code>Stil sayfası sürümü 1,1 olarak ayarlandıysa, yapı verileri sıralayamadı.</span><span class="sxs-lookup"><span data-stu-id="6d25c-105">The <code>xsl:sort</code> construct failed to sort data if the style sheet version was set to 1.1.</span></span></li></ul><span data-ttu-id="6d25c-106">.NET Framework 4,5 ' de, bu sorunlar düzeltildi ve XSLT 1,0 ileri uyumluluk modu düzgün şekilde çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d25c-106">In the .NET Framework 4.5, these issues have been fixed, and XSLT 1.0 forward compatibility mode works properly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6d25c-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="6d25c-107">Suggestion</span></span>

<span data-ttu-id="6d25c-108">Çoğu uygulama etkilenmemelidir, ancak bazı durumlarda veriler farklı sıralanacaktır çünkü artık xsl: Sort kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d25c-108">Most apps should be unaffected, however data will be sorted differently in some cases now that xsl:sort is respected.</span></span> <span data-ttu-id="6d25c-109"><code>xsl:sort</code>1,1 Stil sayfalarında kullanılırsa, uygulamaların sıralanmamış veri sırasına bağlı olmadığını onaylayın.</span><span class="sxs-lookup"><span data-stu-id="6d25c-109">If <code>xsl:sort</code> is used in 1.1 style sheets, confirm that apps were not depending on the unsorted order of data.</span></span> <span data-ttu-id="6d25c-110">Uygulamalar 4,0 sıralama davranışını kullanıyorsa, <code>xsl:sort</code> stil sayfasından kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6d25c-110">If apps rely on the 4.0 sorting behavior, remove <code>xsl:sort</code> from the style sheet.</span></span>

| <span data-ttu-id="6d25c-111">Name</span><span class="sxs-lookup"><span data-stu-id="6d25c-111">Name</span></span>    | <span data-ttu-id="6d25c-112">Değer</span><span class="sxs-lookup"><span data-stu-id="6d25c-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6d25c-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6d25c-113">Scope</span></span>   |<span data-ttu-id="6d25c-114">Edge</span><span class="sxs-lookup"><span data-stu-id="6d25c-114">Edge</span></span>|
|<span data-ttu-id="6d25c-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6d25c-115">Version</span></span>|<span data-ttu-id="6d25c-116">4,5</span><span class="sxs-lookup"><span data-stu-id="6d25c-116">4.5</span></span>|
|<span data-ttu-id="6d25c-117">Tür</span><span class="sxs-lookup"><span data-stu-id="6d25c-117">Type</span></span>|<span data-ttu-id="6d25c-118">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="6d25c-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6d25c-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6d25c-119">Affected APIs</span></span>

-<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|

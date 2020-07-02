---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620688"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="5eba5-101">FlowDocument, ek bir metin satırı gösterebilir</span><span class="sxs-lookup"><span data-stu-id="5eba5-101">FlowDocument may show an extra line of text</span></span>

#### <a name="details"></a><span data-ttu-id="5eba5-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5eba5-102">Details</span></span>

<span data-ttu-id="5eba5-103">Bazı durumlarda, bir <xref:System.Windows.Documents.FlowDocument> öğesi .NET Framework 4,5 üzerinde çalışırken, .NET Framework 4,0 ' de çalışırken nasıl görüntülenmesiyle karşılaştırıldığında ek bir metin satırı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5eba5-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="5eba5-104">Değişikliğin bilinen bir durumu, herhangi bir metnin kötü veya okunaklı görüntülenmesine neden olur, ancak bu, metnin daha önce bir görünümden atlandığı görünmesine neden olabilir <xref:System.Windows.Documents.FlowDocument> .</span><span class="sxs-lookup"><span data-stu-id="5eba5-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5eba5-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="5eba5-105">Suggestion</span></span>

<span data-ttu-id="5eba5-106">Bazı durumlarda, görüntüleme öğesinin PageHeight özelliğini tek tek düşürmek, görüntülenen önceki satır sayısını geri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5eba5-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>

| <span data-ttu-id="5eba5-107">Name</span><span class="sxs-lookup"><span data-stu-id="5eba5-107">Name</span></span>    | <span data-ttu-id="5eba5-108">Değer</span><span class="sxs-lookup"><span data-stu-id="5eba5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5eba5-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5eba5-109">Scope</span></span>   |<span data-ttu-id="5eba5-110">Edge</span><span class="sxs-lookup"><span data-stu-id="5eba5-110">Edge</span></span>|
|<span data-ttu-id="5eba5-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5eba5-111">Version</span></span>|<span data-ttu-id="5eba5-112">4,5</span><span class="sxs-lookup"><span data-stu-id="5eba5-112">4.5</span></span>|
|<span data-ttu-id="5eba5-113">Tür</span><span class="sxs-lookup"><span data-stu-id="5eba5-113">Type</span></span>|<span data-ttu-id="5eba5-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5eba5-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5eba5-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5eba5-115">Affected APIs</span></span>

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|

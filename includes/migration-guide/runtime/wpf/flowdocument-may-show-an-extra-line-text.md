---
ms.openlocfilehash: 6c1740df66ead271afa5f97dc125587810946bc6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981692"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="c2e44-101">FlowDocument fazladan bir satır metin gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c2e44-101">FlowDocument may show an extra line of text</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c2e44-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c2e44-102">Details</span></span>|<span data-ttu-id="c2e44-103">Bazı durumlarda, bir <xref:System.Windows.Documents.FlowDocument> .NET Framework 4.5, .NET Framework 4. 0'çalıştırdığınızda görüntülenme için karşılaştırıldığında üzerinde çalışırken öğe metin fazladan bir satır görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c2e44-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="c2e44-104">Hatalı veya okunaklı olmama görüntülenecek herhangi bir metin neden değişikliği bilinen çalışması yok, ancak, daha önce gelen atlandı görünmesini sağlayabilir bir <xref:System.Windows.Documents.FlowDocument>kullanıcının görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="c2e44-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>|
|<span data-ttu-id="c2e44-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="c2e44-105">Suggestion</span></span>|<span data-ttu-id="c2e44-106">Bazı durumlarda, bir görüntü öğenin PageHeight özelliği azalan önceki görüntülenen satırların sayısı geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2e44-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>|
|<span data-ttu-id="c2e44-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c2e44-107">Scope</span></span>|<span data-ttu-id="c2e44-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="c2e44-108">Edge</span></span>|
|<span data-ttu-id="c2e44-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c2e44-109">Version</span></span>|<span data-ttu-id="c2e44-110">4,5</span><span class="sxs-lookup"><span data-stu-id="c2e44-110">4.5</span></span>|
|<span data-ttu-id="c2e44-111">Tür</span><span class="sxs-lookup"><span data-stu-id="c2e44-111">Type</span></span>|<span data-ttu-id="c2e44-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="c2e44-112">Runtime</span></span>|
|<span data-ttu-id="c2e44-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c2e44-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|

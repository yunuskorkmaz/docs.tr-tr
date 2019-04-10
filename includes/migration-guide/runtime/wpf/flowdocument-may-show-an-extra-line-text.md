---
ms.openlocfilehash: 6c1740df66ead271afa5f97dc125587810946bc6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235804"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument fazladan bir satır metin gösterebilir.

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, bir <xref:System.Windows.Documents.FlowDocument> .NET Framework 4.5, .NET Framework 4. 0'çalıştırdığınızda görüntülenme için karşılaştırıldığında üzerinde çalışırken öğe metin fazladan bir satır görüntülenir. Hatalı veya okunaklı olmama görüntülenecek herhangi bir metin neden değişikliği bilinen çalışması yok, ancak, daha önce gelen atlandı görünmesini sağlayabilir bir <xref:System.Windows.Documents.FlowDocument>kullanıcının görüntüleyin.|
|Öneri|Bazı durumlarda, bir görüntü öğenin PageHeight özelliği azalan önceki görüntülenen satırların sayısı geri yükleyebilirsiniz.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|

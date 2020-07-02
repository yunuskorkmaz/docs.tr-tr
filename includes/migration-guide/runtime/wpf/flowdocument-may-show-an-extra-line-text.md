---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620688"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument, ek bir metin satırı gösterebilir

#### <a name="details"></a>Ayrıntılar

Bazı durumlarda, bir <xref:System.Windows.Documents.FlowDocument> öğesi .NET Framework 4,5 üzerinde çalışırken, .NET Framework 4,0 ' de çalışırken nasıl görüntülenmesiyle karşılaştırıldığında ek bir metin satırı görüntüler. Değişikliğin bilinen bir durumu, herhangi bir metnin kötü veya okunaklı görüntülenmesine neden olur, ancak bu, metnin daha önce bir görünümden atlandığı görünmesine neden olabilir <xref:System.Windows.Documents.FlowDocument> .

#### <a name="suggestion"></a>Öneri

Bazı durumlarda, görüntüleme öğesinin PageHeight özelliğini tek tek düşürmek, görüntülenen önceki satır sayısını geri yükleyebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|

---
ms.openlocfilehash: a61005e317020c47a283dae292236624ec6057ce
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497197"
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
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Documents.FlowDocument.%23ctor>
- <xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)>
- <xref:System.Windows.Controls.FlowDocumentReader.%23ctor>
- <xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor>
- <xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor>

<!--

#### Affected APIs

- `M:System.Windows.Documents.FlowDocument.#ctor`
- `M:System.Windows.Documents.FlowDocument.#ctor(System.Windows.Documents.Block)`
- `M:System.Windows.Controls.FlowDocumentReader.#ctor`
- `M:System.Windows.Controls.FlowDocumentPageViewer.#ctor`
- `M:System.Windows.Controls.Primitives.DocumentPageView.#ctor`

-->

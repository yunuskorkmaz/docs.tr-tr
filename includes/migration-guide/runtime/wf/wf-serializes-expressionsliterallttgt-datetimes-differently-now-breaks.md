---
ms.openlocfilehash: 335647f899c79eff22e313fa40b2e2a73e7cfff0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805233"
---
### <a name="wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serileştiren Expressions.Literal\<T > tarih/saat farklı artık (özel XAML ayrıştırıcıları sonu)

|   |   |
|---|---|
|Ayrıntılar|İlişkili <xref:System.Windows.Markup.ValueSerializer> nesnesi bir <xref:System.DateTime?displayProperty=name> veya <xref:System.DateTimeOffset?displayProperty=name> ikinci nesnesi ve <xref:System.DateTime.Millisecond?displayProperty=name> bileşenleri sıfır olmayan ve (için bir <xref:System.DateTime?displayProperty=name> değer), <xref:System.DateTime.Kind> özelliği için özellik öğesi belirtilmeyen değil bir dize yerine söz dizimi. Bu değişiklik sağlayan <xref:System.DateTime?displayProperty=name> ve <xref:System.DateTimeOffset?displayProperty=name> değerlerinin gidiş dönüşlü olmasına olanak. Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.|
|Öneri|Bu değişiklik sağlayan <xref:System.DateTime?displayProperty=name> ve <xref:System.DateTimeOffset?displayProperty=name> değerlerinin gidiş dönüşlü olmasına olanak. Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

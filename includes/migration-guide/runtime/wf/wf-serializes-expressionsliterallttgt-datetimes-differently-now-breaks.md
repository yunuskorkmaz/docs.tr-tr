---
ms.openlocfilehash: 06424c4fa40343a881356c20003300f65e93efbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497297"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF deyimleri seri hale getirir. sabit değerli &lt; T &gt; DateTimeS Now (özel xaml ayrıştırıcılarını keser)

#### <a name="details"></a>Ayrıntılar

İlişkili <xref:System.Windows.Markup.ValueSerializer> nesne, <xref:System.DateTime?displayProperty=fullName> <xref:System.DateTimeOffset?displayProperty=fullName> ikinci ve bileşenleri sıfır olmayan bir veya nesnesi <xref:System.DateTime.Millisecond?displayProperty=fullName> (bir değer için), özelliği de <xref:System.DateTime?displayProperty=fullName> <xref:System.DateTime.Kind> bir dize yerine özellik öğesi söz dizimine belirtilmemiş olarak dönüştürecek. Bu değişiklik <xref:System.DateTime?displayProperty=fullName> , ve <xref:System.DateTimeOffset?displayProperty=fullName> değerlerinin yuvarlak olarak değiştirilmesini sağlar. Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.

#### <a name="suggestion"></a>Öneri

Bu değişiklik <xref:System.DateTime?displayProperty=fullName> , ve <xref:System.DateTimeOffset?displayProperty=fullName> değerlerinin yuvarlak olarak değiştirilmesini sağlar. Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

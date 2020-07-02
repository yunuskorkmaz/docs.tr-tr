---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620676"
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

---
ms.openlocfilehash: 5c27e8acdf30533036546ba4cca9e06877bde362
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620735"
---
### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT stil sayfası özel durum iletisi değişti

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' de, bir XSLT dosyası çok karmaşık olduğunda hata iletisinin metni, &quot; stil sayfası çok karmaşıktır. &quot; Önceki sürümlerde hata iletisi &quot; XSLT derleme hatası idi. &quot; Hata iletisinin metnine bağlı olan uygulama kodu artık çalışmaz. Ancak, özel durum türleri aynı kalır, bu nedenle bu değişikliğin gerçek bir etkisi olmamalıdır.

#### <a name="suggestion"></a>Öneri

Bu hata koşulundaki özel durum iletisine bağlı olarak herhangi bir uygulama kodunu, yeni iletiyi bekliyor veya (daha da iyi) kodu, yalnızca değişmemiş özel durum türüne () göre güncelleştirin <xref:System.Xml.Xsl.XsltException?displayProperty=fullName> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

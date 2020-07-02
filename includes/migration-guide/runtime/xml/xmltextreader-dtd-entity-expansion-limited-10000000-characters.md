---
ms.openlocfilehash: fdec6671cbf2dae0d72dfaec07f162058b38cf9d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620729"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>XmlTextReader DTD varlık genişletmesi 10.000.000 karakterle sınırlıdır

#### <a name="details"></a>Ayrıntılar

DTD varlık genişletmesi artık 10.000.000 karakterle sınırlıdır. DTD varlık genişletme olmadan veya sınırlı DTD varlık genişletme ile XML dosyalarının yüklenmesi etkilenmez. 10.000.000 karakteri aşan DTD varlıklarını içeren dosyalar yüklenemedi ve şimdi bir özel durum oluşturdu.

#### <a name="suggestion"></a>Öneri

DTD varlık genişletmesi sınırı çok düşük 10.000.000 ise, bu değer özelliği ile geçersiz kılınabilir <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> . <xref:System.Xml.XmlReaderSettings?displayProperty=fullName>Uygun değere sahip olan bir, <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> <code>XmlReader.Create</code> <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (IE <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)> ) ile birlikte geçirilebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)></li></ul>|

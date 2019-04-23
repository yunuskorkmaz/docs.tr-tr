---
ms.openlocfilehash: 1f5bc43dcba15c28c179b23352558411f511c82f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981704"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>XmlTextReader DTD varlık genişletme, 10.000.000 karakterle sınırlıdır

|   |   |
|---|---|
|Ayrıntılar|DTD varlık genişletme, artık 10.000.000 karakterle sınırlıdır. DTD varlık genişletme olmadan veya sınırlı DTD varlık genişletme ile XML dosyalarının yüklenmesi etkilenmez. 10.000.000 karakteri aşan DTD varlıklarını içeren dosyalar yüklenemedi ve şimdi bir özel durum oluşturdu.|
|Öneri|DTD varlık genişletme sınırının çok düşük 10,000,000 ise, değer ile geçersiz kılınabilip <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> özelliği. Bir <xref:System.Xml.XmlReaderSettings?displayProperty=name> uygun ile <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=name> değeri geçilebilir <code>XmlReader.Create</code> alan <xref:System.Xml.XmlReaderSettings?displayProperty=name> (örn. <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)?displayProperty=nameWithType></li></ul>|

---
title: XslTransform Çıkışları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6c2ea2fe2f02dc1897cb1348f4c2585b730036
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924963"
---
# <a name="outputs-from-an-xsltransform"></a>XslTransform Çıkışları
Stil sayfaları, `<xsl:output>` `method` özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden, aşağıdaki tabloda çıktı biçiminin çıktıyı yazmak için ne zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> kullanıldığı ve çıkış biçiminin <xref:System.IO.Stream> veya<xref:System.IO.TextWriter>olarak bildirilmiştir.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Stil sayfaları, `<xsl:output>` `method` özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden, aşağıdaki tabloda çıktı biçiminin çıktıyı yazmak için ne zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> kullanıldığı ve çıkış biçiminin <xref:System.IO.Stream> veya<xref:System.IO.TextWriter>olarak bildirilmiştir. Aşağıdaki tabloda, bir çıkış türü bir <xref:System.Xml.Xsl.XslTransform.Transform%2A> `<xsl:output>` deyimin kullanımıyla birlikte yöntemi tarafından bildirildiğinde ne olacağı açıklanmaktadır:  
  
|\<xsl: output yöntemi = > özniteliği|Sonuç biçimi|  
|-----------------------------------------|-------------------|  
|method = "xml"|XML|  
|method="html"|HTML|  
|method = "metin"|Metin|  
  
> [!NOTE]
> Not: Yöntemi, <xref:System.Xml.XmlReader> yönteminin çıktısı birveya<xref:System.Xml.XmlWriter>olduğunda yoksayılır. `<xsl:output>` <xref:System.Xml.Xsl.XslTransform.Transform%2A>  
  
 Aşağıdaki öznitelikler, ya da <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntem çıktısı bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>olduğunda desteklenir:  
  
- şifreleme  
  
- XML bildirimini atla  
  
- bağımsız  
  
- doctype-genel  
  
- DOCTYPE-System  
  
- CDATA-bölüm-öğeler  
  
- leyebilirsiniz  
  
    > [!NOTE]
    > \*<xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntem, çıkışını bir <xref:System.IO.TextWriter>öğesine gönderirken kodlama özniteliği yok sayılır. Bunun yerine kodlama özelliği <xref:System.IO.TextWriter> kullanılır. 
  
 Aşağıdaki öznitelik, <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntem çıktısı bir <xref:System.IO.Stream>olduğunda yok sayılır:  
  
- Sürüm: sürüm her zaman 1,0  
  
- medya-türü: medya türü  
  
## <a name="escaping-special-characters"></a>Özel karakterleri kaçış  
 Etiketi, özel karakterlerin bir XML biçimine (örneğin, `"<"` simgenin yerine kullanılması `<&lt>` ) veya mevcut koşulda sola atlanıp atlanmayacağını belirtmek için kullanılır. `<xsl:text disable-output-escaping>` Özniteliği bir <xref:System.Xml.XmlReader> veya<xref:System.Xml.XmlWriter> nesnesine dönüştürülürken yok sayılır ve özel karakterler üzerinde hiçbir etkisi olmaz. `disable-output-escaping`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)

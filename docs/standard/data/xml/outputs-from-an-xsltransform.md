---
title: XslTransform Çıkışları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 93cbf7807630a605e17e7f513055c052aad0d08e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159643"
---
# <a name="outputs-from-an-xsltransform"></a>XslTransform Çıkışları
`<xsl:output>` Stil sayfaları, `method` özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden, aşağıdaki tabloda çıktı biçiminin çıktıyı yazmak için ne <xref:System.Xml.Xsl.XslTransform.Transform%2A> zaman kullanıldığı ve çıkış biçiminin de <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>olarak bildirildiği açıklanmaktadır.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler Için Genişletilebilir Stil sayfası DILI (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 `<xsl:output>` Stil sayfaları, `method` özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden, aşağıdaki tabloda çıktı biçiminin çıktıyı yazmak için ne <xref:System.Xml.Xsl.XslTransform.Transform%2A> zaman kullanıldığı ve çıkış biçiminin de <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>olarak bildirildiği açıklanmaktadır. Aşağıdaki tabloda, bir çıkış türü bir <xref:System.Xml.Xsl.XslTransform.Transform%2A> `<xsl:output>` deyimin kullanımıyla birlikte yöntemi tarafından bildirildiğinde ne olacağı açıklanmaktadır:  
  
|\<xsl: output yöntemi = > özniteliği|Sonuç biçimi|  
|-----------------------------------------|-------------------|  
|method = "xml"|XML|  
|method = "html"|HTML|  
|method = "metin"|Metin|  
  
> [!NOTE]
> `<xsl:output>` Note: <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemin çıktısı bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter>olduğunda, ifade yok sayılır.  
  
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
 `<xsl:text disable-output-escaping>` Etiketi, özel KARAKTERLERIN bir XML biçimine (örneğin, `"<"` simgenin yerine kullanılması `<&lt>` ) veya mevcut koşulda sola atlanıp atlanmayacağını belirtmek için kullanılır. `disable-output-escaping` Özniteliği bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesnesine dönüştürülürken yok sayılır ve özel karakterler üzerinde hiçbir etkisi olmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)

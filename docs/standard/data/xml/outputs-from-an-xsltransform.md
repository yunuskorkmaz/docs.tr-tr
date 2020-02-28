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
Stil sayfaları `method` özniteliğiyle `<xsl:output>` bir bildirim kullanarak çıkış biçimini belirleyebildiğinden, aşağıdaki tabloda çıktı biçiminin çıktıyı yazmak için ne <xref:System.Xml.Xsl.XslTransform.Transform%2A> zaman kullanıldığı ve çıkış biçiminin bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>olarak bildirildiği açıklanır.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> sınıfı, .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Stil sayfaları `method` özniteliğiyle `<xsl:output>` bir bildirim kullanarak çıkış biçimini belirleyebildiğinden, aşağıdaki tabloda çıktı biçiminin çıktıyı yazmak için ne <xref:System.Xml.Xsl.XslTransform.Transform%2A> zaman kullanıldığı ve çıkış biçiminin bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>olarak bildirildiği açıklanır. Aşağıdaki tabloda, bir çıkış türü bir `<xsl:output>` deyimin kullanımıyla birlikte <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi tarafından bildirildiğinde ne olacağı açıklanmaktadır:  
  
|\<xsl: output yöntemi = > özniteliği|Sonuç biçimi|  
|-----------------------------------------|-------------------|  
|method = "xml"|XML|  
|method="html"|HTML|  
|method = "metin"|Metin|  
  
> [!NOTE]
> Note: <xref:System.Xml.Xsl.XslTransform.Transform%2A> yönteminin çıktısı bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter>olduğunda `<xsl:output>` ifade yok sayılır.  
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısı bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>olduğunda aşağıdaki öznitelikler desteklenir:  
  
- şifreleme  
  
- XML bildirimini atla  
  
- bağımsız  
  
- doctype-genel  
  
- DOCTYPE-System  
  
- CDATA-bölüm-öğeler  
  
- leyebilirsiniz  
  
    > [!NOTE]
    > \*, <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısını bir <xref:System.IO.TextWriter>gönderirken kodlama özniteliği yok sayılır. Bunun yerine <xref:System.IO.TextWriter> kodlama özelliği kullanılır.
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısı bir <xref:System.IO.Stream>olduğunda aşağıdaki öznitelik yoksayılır:  
  
- Sürüm: sürüm her zaman 1,0  
  
- medya-türü: medya türü  
  
## <a name="escaping-special-characters"></a>Özel karakterleri kaçış  
 `<xsl:text disable-output-escaping>` etiketi, özel karakterlerin bir XML biçimine (örneğin, `"<"` simgenin yerine `<&lt>` kullanılarak) veya mevcut koşulda sola atlanıp atlanmayacağını belirtmek için kullanılır. `disable-output-escaping` özniteliği, bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesnesine dönüştürülürken yok sayılır ve özel karakterler üzerinde hiçbir etkisi olmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)

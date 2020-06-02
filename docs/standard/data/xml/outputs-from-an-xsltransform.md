---
title: XslTransform Çıkışları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 5fa8c8228382f7f326a8d2243ed0450fca31f6fb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288699"
---
# <a name="outputs-from-an-xsltransform"></a>XslTransform Çıkışları
Stil sayfaları, özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden `<xsl:output>` `method` , aşağıdaki tabloda çıktı biçiminin <xref:System.Xml.Xsl.XslTransform.Transform%2A> çıktıyı yazmak için ne zaman kullanıldığı ve çıkış biçiminin de veya olarak bildirildiği açıklanmaktadır <xref:System.IO.Stream> <xref:System.IO.TextWriter> .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .  
  
 Stil sayfaları, özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden `<xsl:output>` `method` , aşağıdaki tabloda çıktı biçiminin <xref:System.Xml.Xsl.XslTransform.Transform%2A> çıktıyı yazmak için ne zaman kullanıldığı ve çıkış biçiminin de veya olarak bildirildiği açıklanmaktadır <xref:System.IO.Stream> <xref:System.IO.TextWriter> . Aşağıdaki tabloda, bir çıkış türü <xref:System.Xml.Xsl.XslTransform.Transform%2A> bir deyimin kullanımıyla birlikte yöntemi tarafından bildirildiğinde ne olacağı açıklanmaktadır `<xsl:output>` :  
  
|\<xsl:output method = > özniteliği|Sonuç biçimi|  
|-----------------------------------------|-------------------|  
|method = "xml"|XML|  
|method = "html"|HTML|  
|method = "metin"|Metin|  
  
> [!NOTE]
> Note: `<xsl:output>` yöntemin çıktısı bir veya olduğunda, ifade yok sayılır <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .  
  
 Aşağıdaki öznitelikler, <xref:System.Xml.Xsl.XslTransform.Transform%2A> ya da yöntem çıktısı bir veya olduğunda desteklenir <xref:System.IO.Stream> <xref:System.IO.TextWriter> :  
  
- şifreleme  
  
- XML bildirimini atla  
  
- bağımsız  
  
- doctype-genel  
  
- DOCTYPE-System  
  
- CDATA-bölüm-öğeler  
  
- leyebilirsiniz  
  
    > [!NOTE]
    > \*<xref:System.Xml.Xsl.XslTransform.Transform%2A>Yöntem, çıkışını bir öğesine gönderirken kodlama özniteliği yok sayılır <xref:System.IO.TextWriter> . <xref:System.IO.TextWriter>Bunun yerine kodlama özelliği kullanılır.
  
 Aşağıdaki öznitelik, <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntem çıktısı bir olduğunda yok sayılır <xref:System.IO.Stream> :  
  
- Sürüm: sürüm her zaman 1,0  
  
- medya-türü: medya türü  
  
## <a name="escaping-special-characters"></a>Özel karakterleri kaçış  
 `<xsl:text disable-output-escaping>`Etiketi, özel karakterlerin BIR XML biçimine (örneğin, `<&lt>` simgenin yerine kullanılması) veya mevcut koşulda sola atlanıp atlanmayacağını belirtmek için kullanılır `"<"` . `disable-output-escaping`Özniteliği bir veya nesnesine dönüştürülürken yok sayılır <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> ve özel karakterler üzerinde hiçbir etkisi olmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)

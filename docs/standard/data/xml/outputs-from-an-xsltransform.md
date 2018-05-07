---
title: Bir çok çıkışlarından
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd22d59375a46c267c6df70727d9ca52e6843214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="outputs-from-an-xsltransform"></a>Bir çok çıkışlarından
Stil sayfaları çıktı biçimi kullanarak belirleyebilirsiniz bu yana bir `<xsl:output>` deyimiyle `method` özniteliği, aşağıdaki tabloda açıklanmaktadır çıkış biçimi olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkışını yazmak için kullanılır ve çıktı biçimi olarak bildirilen bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Stil sayfaları çıktı biçimi kullanarak belirleyebilirsiniz bu yana bir `<xsl:output>` deyimiyle `method` özniteliği, aşağıdaki tabloda açıklanmaktadır çıkış biçimi olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkışını yazmak için kullanılır ve çıktı biçimi olarak bildirilen bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>. Aşağıdaki tabloda bir çıktı türü olarak bildirilmiş ne olur açıklanmaktadır <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi kullanımı ile birlikte bir `<xsl:output>` deyimi:  
  
|\<önceliğiyle yöntemi = > özniteliği|Sonuç biçimi|  
|-----------------------------------------|-------------------|  
|yöntem = "xml"|XML|  
|method="html"|HTML|  
|yöntem = "text"|Metin|  
  
> [!NOTE]
>  Not: `<xsl:output>` deyimi göz ardı edilir zaman çıktısını <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter>.  
  
 Aşağıdaki öznitelikler desteklenen zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısı bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>:  
  
-   kodlama *  
  
-   atlayın-xml-bildirimi  
  
-   bağımsız  
  
-   doctype-genel  
  
-   Sistem dışı doctype  
  
-   CDATA bölümü öğeleri  
  
-   Girinti  
  
    > [!NOTE]
    >  * kodlama özniteliği göz ardı zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısını için gönderme bir <xref:System.IO.TextWriter>. Kodlama özelliği <xref:System.IO.TextWriter> onun yerine kullanılır.  
  
 Aşağıdaki öznitelik yoksayılır zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısı bir <xref:System.IO.Stream>:  
  
-   Sürüm: sürümüdür 1.0 her zaman  
  
-   Media-type: medya türü  
  
## <a name="escaping-special-characters"></a>Kaçış özel karakterleri  
 `<xsl:text disable-output-escaping>` Etiketi özel karakterler bir XML forma kaçış gerek olmadığını belirtmek için kullanılır (örneğin, kullanarak `<&lt>` yerine `"<"` simgesi) veya mevcut koşulunda sol. `disable-output-escaping` Özniteliği göz ardı edilir için dönüştürülürken bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesne ve özel karakterler üzerinde hiçbir etkisi olmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)

---
title: XslTransform çıkışları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b299f09f3dc47b5d136284d4d1d285f2e5aad5f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268016"
---
# <a name="outputs-from-an-xsltransform"></a>XslTransform çıkışları
Stil sayfaları kullanıp çıkış biçimini belirlemek bu yana bir `<xsl:output>` deyimiyle `method` öznitelik, aşağıdaki tabloda açıklanmaktadır çıkış biçimini olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkışını yazmak için kullanılır ve çıkış biçimi olarak bildirilen bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Stil sayfaları kullanıp çıkış biçimini belirlemek bu yana bir `<xsl:output>` deyimiyle `method` öznitelik, aşağıdaki tabloda açıklanmaktadır çıkış biçimini olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkışını yazmak için kullanılır ve çıkış biçimi olarak bildirilen bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>. Aşağıdaki tabloda bir çıkış türü olarak bildirilmiş bıraktığınızda ne olacağı açıklanır <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi kullanımı ile birlikte bir `<xsl:output>` deyimi:  
  
|\<önceliğiyle yöntemi = > öznitelik|Sonuç biçimi|  
|-----------------------------------------|-------------------|  
|yöntem = "xml"|XML|  
|method="html"|HTML|  
|yöntem = "text"|Metin|  
  
> [!NOTE]
>  Not: `<xsl:output>` deyimi göz ardı edilir olduğunda çıktısını <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter>.  
  
 Aşağıdaki öznitelikler desteklenen zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkış bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>:  
  
-   kodlama *  
  
-   atlayın-xml-bildirimi  
  
-   bağımsız  
  
-   doctype-genel  
  
-   Sistem dışı doctype  
  
-   CDATA bölümü öğeleri  
  
-   Girinti  
  
    > [!NOTE]
    >  * kodlama özniteliği göz ardı edilir olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> çıktısını için gönderme yöntemi bir <xref:System.IO.TextWriter>. Kodlama özelliği <xref:System.IO.TextWriter> yerine kullanılır.  
  
 Aşağıdaki özniteliği göz ardı edilir olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkış bir <xref:System.IO.Stream>:  
  
-   Sürüm: sürüm 1.0 her zaman olur.  
  
-   medya türü: medya türü  
  
## <a name="escaping-special-characters"></a>Kaçış özel karakterleri  
 `<xsl:text disable-output-escaping>` Etiketi, özel karakterler bir XML forma çizgilerin aşağıdaki gibi ihtiyacınız olup olmadığını belirtmek için kullanılır (örneğin, kullanarak `<&lt>` yerine `"<"` sembol) veya mevcut koşulunda sol. `disable-output-escaping` Özniteliği yok sayıldı için dönüştürürken bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesne ve özel karakterler üzerinde hiçbir etkisi olmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)

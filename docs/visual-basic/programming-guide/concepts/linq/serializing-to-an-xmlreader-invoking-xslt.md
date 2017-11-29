---
title: XmlReader (bildirilecekse XSLT) seri hale getirme (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea4a8a17e938b22d6e307ebe307c69481e44e6d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>XmlReader (bildirilecekse XSLT) seri hale getirme (Visual Basic)
Kullandığınızda <xref:System.Xml?displayProperty=nameWithType> birlikte çalışabilirlik özelliklerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], kullanabileceğiniz <xref:System.Xml.Linq.XNode.CreateReader%2A> oluşturmak için bir <xref:System.Xml.XmlReader>. Öğesinden okur Modülü <xref:System.Xml.XmlReader> düğümleri XML ağacından okur ve bunları uygun şekilde işler.  
  
## <a name="invoking-an-xslt-transformation"></a>XSLT dönüşümü çağırma  
 XSLT dönüşümü çağrılırken, bu yöntem bir olası kullanımı içindir. Bir XML ağacı oluşturma, oluşturma bir <xref:System.Xml.XmlReader> XML ağacından bir yeni belge oluşturun ve ardından oluşturmak bir <xref:System.Xml.XmlWriter> yeni belgesine yazılacak. Daha sonra tümleştirilmesidir XSLT dönüşümü çağırabileceği <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>. Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşüm sonuçları ile doldurulur.  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>  
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendiricisi XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)

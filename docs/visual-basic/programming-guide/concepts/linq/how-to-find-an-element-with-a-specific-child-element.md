---
title: 'Nasıl yapılır: Belirli Bir Alt Öğeye Sahip Öğeyi Bulma'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: a05504070fe3d2ea5eb6135fd3bf697b131686c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405293"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a>Nasıl yapılır: belirli bir alt öğeye sahip bir öğe bulma (Visual Basic)
Bu konu, belirli bir değere sahip bir alt öğesi olan belirli bir öğenin nasıl bulunacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Örnek, `Test` `CommandLine` "EXAMP2. exe" değerine sahip bir alt öğesi olan öğesini bulur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: test yapılandırması (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
0002  
0006  
```  
  
 Bu örnekte XML [alt eksen özelliği](../../../language-reference/xml-axis/xml-child-axis-property.md), [XML özniteliği eksen özelliği](../../../language-reference/xml-axis/xml-attribute-axis-property.md)ve [XML değeri özelliği](../../../language-reference/xml-axis/xml-value-property.md)kullanılmıştır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında test yapılandırması](sample-xml-file-test-configuration-in-a-namespace.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Temel sorgular (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Projeksiyon Işlemleri (Visual Basic)](projection-operations.md)

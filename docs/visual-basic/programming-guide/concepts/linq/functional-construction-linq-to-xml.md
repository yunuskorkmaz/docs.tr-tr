---
title: İşlevsel Oluşturma (LINQ to XML) Karşılaştırması
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: 6366c7781372d34e15d62f81a5ceae8ff4ccda2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353463"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>İşlevsel oluşturma (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] *işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar. İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturma olanağıdır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabiriminin işlevsel oluşturmayı etkinleştiren birkaç temel özelliği vardır:  
  
- <xref:System.Xml.Linq.XElement> Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır. Örneğin, bir alt öğe haline gelen başka bir <xref:System.Xml.Linq.XElement> nesnesini geçirebilirsiniz. Öğesinin bir özniteliği haline gelen bir <xref:System.Xml.Linq.XAttribute> nesnesini geçirebilirsiniz. Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.  
  
- <xref:System.Xml.Linq.XElement> Oluşturucu <xref:System.Object>türünde bir `params` dizisi alır, böylece oluşturucuya herhangi bir sayıda nesne geçirebilirsiniz. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.  
  
- Bir nesne <xref:System.Collections.Generic.IEnumerable%601>uygularsa, nesnedeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir. Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı olarak eklenir. Bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.  
  
 Aşağıda bir örnek verilmiştir:  
  
 Bu özellikler, XML ağacı oluşturmak için XML değişmez değerleri kullanarak kod yazmanızı ve ayrıca bir XML ağacı oluştururken [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgularının sonuçlarını kullanan kodu yazmanızı sağlar:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

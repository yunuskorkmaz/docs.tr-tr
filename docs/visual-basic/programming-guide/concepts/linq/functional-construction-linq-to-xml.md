---
title: İşlevsel oluşturma (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: a942d4a0fa4c33cf4699c5825ea05403bdfce48f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64618330"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>İşlevsel oluşturma (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] adlı XML öğeleri oluşturmak için güçlü bir yol sağlar *işlevsel oluşturma*. Tek bir deyimde bir XML ağacı oluşturma olanağı işlevsel yapısıdır.  
  
 Birkaç temel özellikleri vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma sağlayan bir programlama arabirimi:  
  
- <xref:System.Xml.Linq.XElement> Oluşturucusu, çeşitli içerik için bağımsız değişkenleri alır. Örneğin, başka bir geçirebilirsiniz <xref:System.Xml.Linq.XElement> bir alt öğesi olan nesne. Geçirebilirsiniz bir <xref:System.Xml.Linq.XAttribute> öğesinin bir özniteliği olan nesne. Veya başka türde bir nesne bir dizeye dönüştürülür ve öğenin metin içeriğini olur geçirebilirsiniz.  
  
- <xref:System.Xml.Linq.XElement> Oluşturucusu alır bir `params` türünde dizi <xref:System.Object>, böylece herhangi bir sayıda nesneleri için oluşturucu geçirebilirsiniz. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.  
  
- Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>, koleksiyon nesnesi içinde listelenmiş ve koleksiyondaki tüm öğelerin eklenir. Koleksiyon içeriyorsa <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler, koleksiyondaki her öğe ayrı olarak eklenir. Sonuçlarını geçirmenize izin verdiğinden, bu önemli bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Sorgu Oluşturucusu.  
  
 Bir örnek verilmiştir:  
  
 Bu özellikler bir XML ağacı oluşturmak için ve ayrıca sonuçları kullanan kod yazmak için XML değişmez değerlerini kullanarak kod yazmanıza olanak verir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular bir XML ağacı oluşturduğunuzda:  
  
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

- [XML ağaçları (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

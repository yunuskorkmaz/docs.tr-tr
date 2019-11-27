---
title: 'Nasıl yapılır: bağlam temelinde öğeleri bulan bir sorgu yazma'
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: d25c6d47eee2ae092c84c3db3c08c3e21e7d98d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346213"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a>Nasıl yapılır: bağlam temelinde öğeleri bulan bir sorgu yazma (Visual Basic)
Bazen, bağlamlarına göre öğeleri seçen bir sorgu yazmanız gerekebilir. Önceki veya sonraki eşdüzey öğelere göre filtrelemek isteyebilirsiniz. Alt veya üst öğe öğelerine göre filtrelemek isteyebilirsiniz.  
  
 Bunu bir sorgu yazarak ve `where` yan tümcesindeki sorgunun sonuçlarını kullanarak yapabilirsiniz. İlk olarak null ile test etmeniz ve sonra değeri test etmeniz gerekiyorsa, sorguyu bir `let` yan tümcesinde yapmak daha uygundur ve sonra sonuçları `where` yan tümcesinde kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `ul` öğesi tarafından hemen izlenen tüm `p` öğelerini seçer.  
  
```vb  
Dim doc As XElement = _  
    <Root>  
        <p id='1'/>  
        <ul>abc</ul>  
        <Child>  
            <p id='2'/>  
            <notul/>  
            <p id='3'/>  
            <ul>def</ul>  
            <p id='4'/>  
        </Child>  
        <Child>  
            <p id='5'/>  
            <notul/>  
            <p id='6'/>  
            <ul>abc</ul>  
            <p id='7'/>  
        </Child>  
    </Root>  
  
Dim items As IEnumerable(Of XElement) = _  
    From e In doc...<p> _  
    Let z = e.ElementsAfterSelf().FirstOrDefault() _  
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _  
    Select e  
  
For Each e As XElement In items  
    Console.WriteLine("id = {0}", e.@<id>)  
Next  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim doc As XElement = _  
            <Root>  
                <p id='1'/>  
                <ul>abc</ul>  
                <Child>  
                    <p id='2'/>  
                    <notul/>  
                    <p id='3'/>  
                    <ul>def</ul>  
                    <p id='4'/>  
                </Child>  
                <Child>  
                    <p id='5'/>  
                    <notul/>  
                    <p id='6'/>  
                    <ul>abc</ul>  
                    <p id='7'/>  
                </Child>  
            </Root>  
  
        Dim items As IEnumerable(Of XElement) = _  
            From e In doc...<p> _  
            Let z = e.ElementsAfterSelf().FirstOrDefault() _  
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _  
            Select e  
  
        For Each e As XElement In items  
            Console.WriteLine("id = {0}", e.@<id>)  
        Next  
    End Sub  
End Module  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [Temel sorgular (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

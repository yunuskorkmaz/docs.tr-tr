---
title: 'Nasıl yapılır: ad alanlarında XML üzerinde sorgu yazma'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 496cf8daf5136e8aafff000312bbd730a5152e9f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344466"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Nasıl yapılır: ad alanlarında XML üzerinde sorgu yazma (Visual Basic)
Bir ad alanında olan XML üzerinde bir sorgu yazmak için, doğru ad alanına sahip <xref:System.Xml.Linq.XName> nesneleri kullanmanız gerekir.  
  
 Visual Basic, en yaygın yaklaşım genel bir ad alanı tanımlamaktır ve sonra genel ad alanını kullanan XML değişmez değerlerini ve XML özelliklerini kullanır. Genel bir varsayılan ad alanı tanımlayabilirsiniz. Bu durumda, XML sabit değerlerinde bulunan öğeler varsayılan olarak ad alanında yer alabilir. Alternatif olarak, ön ek içeren bir genel ad alanı tanımlayabilir ve sonra öneki XML sabit değerlerinde ve XML özelliklerinde gereken şekilde kullanabilirsiniz. Diğer XML formlarında olduğu gibi, özniteliklerin her zaman varsayılan olarak ad alanı yoktur.  
  
 Bu konudaki ilk örnek kümesi, varsayılan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir. İkinci küme, öneki olan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan bir ad alanında bulunan bir XML ağacı oluşturur. Daha sonra bir öğe koleksiyonu alır.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
1  
2  
3  
```  
  
## <a name="example"></a>Örnek  
 Ancak Visual Basic ' de, ön ek içeren bir ad alanı kullanan bir XML ağacına sorgu yazmak, varsayılan bir ad alanında bir XML ağacını sorgulamadan oldukça farklıdır. Genellikle `Imports` ifadesini kullanarak ad alanını önekiyle içeri aktarabilirsiniz. Ardından, XML ağacını oluştururken öğesi ve öznitelik adlarında öneki kullanın. Xml özelliklerini kullanarak bir XML ağacını sorgularken de ön eki kullanırsınız.  
  
 Aşağıdaki örnek, öneki olan bir ad alanında olan bir XML ağacı oluşturur. Daha sonra bir öğe koleksiyonu alır.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
1  
2  
3  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)

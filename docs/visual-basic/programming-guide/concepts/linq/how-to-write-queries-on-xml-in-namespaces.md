---
title: "Nasıl yapılır: XML ad alanları (Visual Basic) içinde sorguları yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5708a2a162132262722f390842f59c9c6a6838e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Nasıl yapılır: XML ad alanları (Visual Basic) içinde sorguları yazma
İçinde bir ad alanı XML bir sorgu yazmak için kullanmanız gerekir <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri.  
  
 Visual Basic'te en yaygın genel ad alanı tanımlamak ve XML değişmez değerleri ve genel ad alanı kullanmak XML özellikleri kullanmak için bir yaklaşımdır. Genel varsayılan ad alanı, varsayılan olarak ad alanında XML değişmez değerleri öğelerinde; Bu durumda olacaktır tanımlayabilirsiniz. Alternatif olarak, genel ad alanı öneki tanımlamak ve XML değişmez değerleri ve XML özellikleri gerektiği gibi ön ekini kullanın. Formlarla diğer XML gibi her zaman varsayılan olarak hiçbir ad alanındaki öznitelikleridir.  
  
 Bu konudaki örnekler ilk kümesi varsayılan ad alanında bir XML ağacı oluşturulacağını gösterir. İkinci küme öneki bir ad alanındaki bir XML ağacı oluşturulacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur. Ardından, öğe koleksiyonunu alır.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Örnek  
 Visual Basic'te, ancak, bir ad alanı öneki ile kullanan bir XML ağaç sorguları yazma bir varsayılan ad alanı XML ağacında sorgulama oldukça farklıdır. Tipik olarak kullandığınız `Imports` ad alanı öneki almak için deyimi. XML ağaç yapısı oluştururken öğe ve öznitelik adları ön ekini kullanın. XML özellikleri kullanılarak bir XML ağacı sorgulanırken de ön ekini kullanın.  
  
 Aşağıdaki örnek, bir ad alanı öneki bulunduğu bir XML ağacı oluşturur. Ardından, öğe koleksiyonunu alır.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)

---
title: 'Nasıl yapılır: ad alanları (LINQ-XML) ile bir belge oluşturma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Nasıl yapılır: ad alanları (LINQ-XML) ile bir belge oluşturma (Visual Basic)
Bu konu, Visual Basic'de ad alanları ile bir belge oluşturulacağını gösterir.  
  
 Visual Basic'te XML değişmez değerleri kullanırken, kullanıcılar bir genel varsayılan XML ad alanı tanımlayabilirsiniz. Bu ad alanı XML değişmez değerleri ve XML özellikleri için varsayılan ad alanıdır. Varsayılan XML ad alanı da proje düzeyinde veya dosya düzeyinde tanımlanabilir. Dosya düzeyinde tanımlanmış olması durumunda, varsayılan ad alanı proje düzeyinde geçersiz kılar.  
  
 Ayrıca, diğer ad tanımlayın ve bu ad alanları için ad alanı öneklerini belirtin.  
  
 Varsayılan ad alanlarını ve bir önek ile ad alanlarını kullanarak tanımladığınız `Imports` anahtar sözcüğü.  
  
 Daha fazla bilgi için bkz: [Visual Basic'te XML değişmez değerleri giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Varsayılan XML ad alanı yalnızca öğeleri ve öznitelikleri geçerli olduğunu unutmayın. Hiçbir ad alanındaki her zaman varsayılan öznitelikleridir. Ancak, bir ad alanındaki bir öznitelik koymak için bir ad alanı öneki kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanı içeren bir belgeyi oluşturur.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte, biri varsayılan ad olan içeren iki ad alanı, bir belgeyi oluşturur.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ad alanı öneklerini ikisiyle birden çok ad içeren bir belgeyi oluşturur.  
  
 Bir XML ağacı serileştirilirken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] böylece her öğe, belirtilen ad alanında gerektiği gibi ad alanı bildirimleri yayar.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)

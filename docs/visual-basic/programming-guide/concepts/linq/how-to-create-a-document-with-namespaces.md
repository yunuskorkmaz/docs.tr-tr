---
title: 'Nasıl yapılır: Ad alanları (LINQ to XML) ile belge oluşturma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: e0f24b509cdac86f652fb41197c2594b4c474fbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631301"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Nasıl yapılır: Ad alanları (LINQ to XML) ile belge oluşturma (Visual Basic)
Bu konuda, Visual Basic'de ad alanları ile belge oluşturma gösterilmektedir.  
  
 Visual Basic'de XML değişmez değerlerini kullanarak, kullanıcıların bir genel varsayılan XML ad alanı tanımlayabilirsiniz. Bu ad alanı, hem XML sabit değerleri ve XML özellikleri için varsayılan ad alanı. Varsayılan XML ad alanı, proje düzeyinde veya dosya düzeyinde tanımlanabilir. Dosya düzeyinde tanımlanmışsa, varsayılan ad alanı proje düzeyinde geçersiz kılar.  
  
 Ayrıca, diğer ad alanları tanımlayın ve bu ad alanları için ad alanı öneklerini belirtin.  
  
 Varsayılan ad alanları hem de ad alanı öneki kullanarak tanımladığınız `Imports` anahtar sözcüğü.  
  
 Daha fazla bilgi için [Visual Basic'te XML değişmez değerlerine giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Varsayılan XML ad alanı yalnızca öğeler ve öznitelikler için geçerli olduğunu unutmayın. Varsayılan ad alanı yok olarak her zaman öznitelikleridir. Ancak, bir ad alanında bir öznitelik koymak için bir ad alanı öneki kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad uzayını içeren bir belge oluşturulur.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte, biri varsayılan ad alanı iki ad alanları içeren bir belge oluşturulur.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok ad ad alanı öneklerini her ikisini birden içeren bir belge oluşturulur.  
  
 Bir XML ağacı serileştirilirken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] her öğe, ayrılmış ad alanı içinde olması gerektiği gibi ad alanı bildirimi yayar.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)

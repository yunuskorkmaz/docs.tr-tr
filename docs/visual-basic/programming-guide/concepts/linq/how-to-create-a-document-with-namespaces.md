---
title: 'Nasıl yapılır: ad alanları ile belge oluşturma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: bbd23840b0356cf14d2c7d6cb71591fe6461a8bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332579"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Nasıl yapılır: ad alanları ile belge oluşturma (LINQ to XML) (Visual Basic)
Bu konu başlığı altında, Visual Basic ad alanları içeren bir belgenin nasıl oluşturulacağı gösterilmektedir.  
  
 Visual Basic XML değişmez değerleri kullanılırken, kullanıcılar bir genel varsayılan XML ad alanı tanımlayabilir. Bu ad alanı, XML değişmez değerleri ve XML özellikleri için varsayılan ad alanıdır. Varsayılan XML ad alanı, proje düzeyinde ya da dosya düzeyinde tanımlanabilir. Dosya düzeyinde tanımlıysa, proje düzeyinde varsayılan ad alanını geçersiz kılar.  
  
 Diğer ad alanlarını da tanımlayabilir ve bu ad alanları için ad alanı öneklerini belirtebilirsiniz.  
  
 `Imports` anahtar sözcüğünü kullanarak, öneki ile hem varsayılan ad alanlarını hem de ad alanlarını tanımlarsınız.  
  
 Daha fazla bilgi için bkz. [VISUAL BASIC XML değişmez değerlerine giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Varsayılan XML ad alanının yalnızca öğeler için geçerli olduğunu ve öznitelikler için geçerli olduğunu unutmayın. Öznitelikler varsayılan olarak her zaman ad alanı değildir. Ancak, bir ad alanına bir özniteliği yerleştirmek için bir ad alanı öneki kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanı içeren bir belge oluşturur.  
  
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
 Bu örnekte, biri varsayılan ad alanı olan iki ad alanı içeren bir belge oluşturulur.  
  
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
 Aşağıdaki örnek, ad alanı önekleri ile birlikte birden çok ad alanı içeren bir belge oluşturur.  
  
 Bir XML ağacını serileştirilirken, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] her bir öğenin belirlenen ad alanında olması için ad alanı bildirimleri gerektiği gibi yayar.  
  
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

- [Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)

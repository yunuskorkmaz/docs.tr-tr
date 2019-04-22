---
title: Genel ad alanları (Visual Basic) (LINQ to XML) ile çalışma
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: d8e74e949815d36f06f522460cc31ca6c3ccabb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827386"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Genel ad alanları (Visual Basic) (LINQ to XML) ile çalışma
Visual Basic'de XML değişmez değerlerini anahtar özelliklerinden biridir özelliği XML ad alanlarını kullanarak bildirme `Imports` deyimi. Bu özelliği kullanarak, bir ön ekini kullanan bir XML ad alanı bildirebilir veya varsayılan XML ad alanı bildirebilirsiniz.  
  
 Bu yetenek, iki durumlarda kullanışlıdır. İlk olarak, XML değişmez değerlerine bildirilen ad alanları katıştırılmış ifadeler taşınmaz. Genel ad alanlarını bildirme katıştırılmış ifadeler ad alanları ile kullanmak için yapmanız gereken iş miktarını azaltır. İkinci olarak, ad alanları XML özellikleri ile kullanmak için genel ad alanları belirtmesi gerekir.  
  
 Genel ad alanları proje düzeyinde bildirebilirsiniz. Proje düzeyi genel ad alanları geçersiz kılmalar Modül düzeyinde genel ad alanları da bildirebilirsiniz. Son olarak, genel ad alanları sabit değeri bir XML geçersiz kılabilirsiniz.  
  
 XML sabit değerleri veya genel olarak bildirilen ad alanlarında XML özellikleri kullandığınızda, Visual Studio'da üzerine gelerek genişletilmiş adını XML sabit değerleri veya özellikleri görebilirsiniz. Genişletilmiş adı bir araç ipucu olarak görürsünüz.  
  
 Alabileceğiniz bir <xref:System.Xml.Linq.XNamespace> kullanarak bir genel ad karşılık gelen nesne `GetXmlNamespace` yöntemi.  
  
## <a name="examples-of-global-namespaces"></a>Genel ad alanları örnekleri  
 Aşağıdaki örnek, kullanarak varsayılan genel bir ad bildirir `Imports` deyimi ve sonra başlatmak için kullandığı bir XML değişmez bir <xref:System.Xml.Linq.XElement> nesne bu ad alanındaki:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 Aşağıdaki örnek bir genel ad alanı öneki ile bildirir ve ardından bir öğe başlatmak için bir XML değişmez değer kullanır:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a>Genel ad alanları ve katıştırılmış ifadeler  
 XML değişmez değerlerine bildirilen ad alanları katıştırılmış ifadeler taşınmaz. Aşağıdaki örnek, bir varsayılan ad alanı bildirir. Katıştırılmış bir ifade kullanır `Child` öğesi.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 Gördüğünüz gibi elde edilen XML varsayılan ad alanı bildirimini içerir. böylece `Child` hiçbir ad alanında bir öğedir.  
  
 Ad alanında bir katıştırılmış deyim şu şekilde yeniden bildirebilirsiniz:  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 Ancak, bu daha iyi bir yaklaşım genel varsayılan ad alanını kullanmak için daha kullanışsız olur. Genel varsayılan ad alanı ile ad alanlarını bildirme olmadan XML sabit değerleri kullanabilirsiniz. Elde edilen XML içinde genel olarak bildirilen varsayılan ad alanı olacaktır.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a>XML özellikleri ile ad alanlarını kullanma  
 XML özellikleri de doğru isim uzayında olacaktır, böylece bir ad alanındaki bir XML ağacı çalıştığınız ve XML özellikleri kullanırsanız, genel bir ad kullanmanız gerekir. Aşağıdaki örnek, bir XML ağacının ad bildirir. Ardından sayısı yazdırır `Child` öğeleri.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Bu örnek olduğunu gösterir. hiçbir `Child` öğeleri. Bu, aşağıdaki çıktıyı üretir:  
  
```  
0  
```  
  
 Ardından ancak varsayılan genel ad alanı bildirirseniz, XML değişmez değer hem XML özelliği varsayılan genel ad alanında şunlardır:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 Bu örnek olduğunu belirten `Child` öğesi. Bu, aşağıdaki çıktıyı üretir:  
  
```  
1  
```  
  
 Bir ön ekine sahip bir genel ad alanı olarak bildirirseniz, XML değişmez değerleri ve XML özellikleri için ön ek kullanabilirsiniz:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace ve genel ad alanları  
 Alabileceğiniz bir <xref:System.Xml.Linq.XNamespace> kullanarak nesne `GetXmlNamespace` yöntemi:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)

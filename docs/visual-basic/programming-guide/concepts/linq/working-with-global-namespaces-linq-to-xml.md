---
title: Genel ad alanları (Visual Basic) ile çalışma (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 9aab6f7175c905fcb3e82829f131f52b3d9368ac
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710379"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Genel ad alanları (Visual Basic) ile çalışma (LINQ to XML)
Visual Basic xml sabit değerlerinin temel özelliklerinden biri, `Imports` ifadesini kullanarak XML ad alanları bildirme yeteneğidir. Bu özelliği kullanarak, ön ek kullanan bir XML ad alanı bildirebilir veya varsayılan bir XML ad alanı bildirebilirsiniz.  
  
 Bu özellik iki durumda yararlıdır. İlk olarak, XML değişmez değerlerinde belirtilen ad alanları, katıştırılmış ifadeler içine taşımaz. Genel ad alanlarını bildirmek, katıştırılmış ifadeleri ad alanlarıyla birlikte kullanmak için yapmanız gereken iş miktarını azaltır. İkincisi, XML özellikleriyle ad alanlarını kullanabilmeniz için genel ad alanlarını bildirmeniz gerekir.  
  
 Genel ad alanlarını proje düzeyinde bildirebilirsiniz. Genel ad alanlarını modül düzeyinde bildirebilirsiniz ve bu da proje düzeyi genel ad alanlarını geçersiz kılar. Son olarak, bir XML sabit değerinde genel ad alanlarını geçersiz kılabilirsiniz.  
  
 Genel olarak tanımlanmış ad alanlarında bulunan XML değişmez değerlerini veya xml özelliklerini kullanırken, Visual Studio 'da üzerine giderek, XML değişmez değerlerinin veya özelliklerinin genişletilmiş adını görebilirsiniz. Genişletilmiş adı bir araç ipucunda görürsünüz.  
  
 Yöntemini kullanarak genel bir <xref:System.Xml.Linq.XNamespace> ad alanına karşılık gelen bir nesnesi alabilirsiniz. `GetXmlNamespace`  
  
## <a name="examples-of-global-namespaces"></a>Genel ad alanı örnekleri  
 Aşağıdaki örnek, bir varsayılan genel ad alanını `Imports` bildirimini kullanarak bildirir ve sonra bu ad alanındaki bir <xref:System.Xml.Linq.XElement> nesneyi başlatmak için bir XML değişmez değeri kullanır:  
  
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
  
 Aşağıdaki örnek bir ön eki olan genel bir ad alanı bildirir ve sonra bir öğeyi başlatmak için bir XML değişmez değeri kullanır:  
  
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
  
## <a name="global-namespaces-and-embedded-expressions"></a>Genel ad alanları ve katıştırılmış Ifadeler  
 XML değişmez değerlerinde belirtilen ad alanları, gömülü ifadeler içine taşımaz. Aşağıdaki örnek bir varsayılan ad alanı bildirir. Daha sonra `Child` öğesi için gömülü bir ifade kullanır.  
  
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
  
 Gördüğünüz gibi, elde edilen XML, bir varsayılan ad alanı bildirimi içerir, böylece `Child` öğe ad alanı içermez.  
  
 Ad alanını katıştırılmış ifadede aşağıdaki gibi yeniden bildirebilirsiniz:  
  
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
  
 Ancak bu, daha iyi bir yaklaşım olan genel varsayılan ad alanından kullanılmak üzere daha kısaberdır. Genel varsayılan ad alanı ile, XML değişmez değerlerini ad alanları bildirmeden kullanabilirsiniz. Elde edilen XML, genel olarak belirtilen varsayılan ad alanında olacaktır.  
  
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
  
## <a name="using-namespaces-with-xml-properties"></a>XML özellikleriyle ad alanlarını kullanma  
 Bir ad alanında olan bir XML ağacıyla çalışıyorsanız ve XML özelliklerini kullanıyorsanız, XML özelliklerinin de doğru ad alanında olması için genel bir ad alanı kullanmanız gerekir. Aşağıdaki örnek, bir ad alanında bir XML ağacını bildirir. Daha sonra `Child` öğe sayısını yazdırır.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Bu örnek, hiçbir `Child` öğe olmadığını gösterir. Aşağıdaki çıktıyı üretir:  
  
```  
0  
```  
  
 Ancak, varsayılan bir genel ad alanı bildirirseniz, hem XML değişmez değeri hem de XML özelliği varsayılan genel ad alanında bulunur:  
  
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
  
 Bu örnek, bir `Child` öğe olduğunu gösterir. Aşağıdaki çıktıyı üretir:  
  
```  
1  
```  
  
 Ön eki olan genel bir ad alanı bildirirseniz, öneki hem XML değişmez değerleri hem de XML özellikleri için kullanabilirsiniz:  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace ve Global ad alanları  
 Yöntemini kullanarak bir <xref:System.Xml.Linq.XNamespace> nesnesi edinebilirsiniz: `GetXmlNamespace`  
  
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

- [Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)

---
title: "Genel ad alanları (Visual Basic) (LINQ-XML) ile çalışma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 376a6d2dfbca22fb8efc6395f478839d716e14d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Genel ad alanları (Visual Basic) (LINQ-XML) ile çalışma
Visual Basic'de XML değişmez değerleri önemli özelliklerinden biridir kullanarak XML ad alanlarını bildirme yeteneği `Imports` deyimi. Bu özelliği kullanarak, bir önek kullanan bir XML ad alanı bildirimini veya varsayılan bir XML ad alanı bildirebilirsiniz.  
  
 Bu özellik, iki durumlarda faydalıdır. İlk olarak, XML değişmez değerlerine bildirilen ad alanları katıştırılmış ifadeler taşınmaz. Genel ad alanlarını bildirme katıştırılmış ifadeler ad alanları ile kullanmak için yapmanız gereken iş miktarını azaltır. İkinci olarak, ad alanları ile XML özellikleri kullanmak için genel ad alanları bildirmeniz gerekir.  
  
 Proje düzeyinde genel ad alanları bildirebilirsiniz. Proje düzeyi genel ad alanları geçersiz kılmaları modülü düzeyinde genel ad alanlarını da bildirebilirsiniz. Son olarak, bir XML değişmez değer genel ad alanları geçersiz kılabilirsiniz.  
  
 XML değişmez değerleri veya genel olarak bildirilen ad alanlarında XML özellikleri kullandığınızda, Visual Studio'da üzerine gelerek genişletilmiş adı XML değişmez değerleri veya özellikler görebilirsiniz. Genişletilmiş ad, bir araç ipucunda görürsünüz.  
  
 Alabileceğiniz bir <xref:System.Xml.Linq.XNamespace> kullanarak genel ad alanı için karşılık gelen nesne `GetXmlNamespace` yöntemi.  
  
## <a name="examples-of-global-namespaces"></a>Genel ad alanları örnekleri  
 Kullanarak aşağıdaki örnekte bir varsayılan genel ad alanı bildirir `Imports` deyimi ve başlatmak için bir XML değişmez değer kullanan bir <xref:System.Xml.Linq.XElement> ad nesnesinde:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 Aşağıdaki örnek, genel bir ad alanı öneki bildirir ve bir öğeyi başlatmak için bir XML değişmez değer kullanır:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a>Genel ad alanları ve katıştırılmış ifadeler  
 XML değişmez değerlerine bildirilen ad alanları katıştırılmış ifadeler taşınmaz. Aşağıdaki örnek, bir varsayılan ad alanı bildirir. Katıştırılmış bir ifadenin ardından kullanan `Child` öğesi.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 Gördüğünüz gibi sonuç XML bir varsayılan ad alanı bildirimini içerir. böylece `Child` hiçbir ad alanında bir öğedir.  
  
 Ad alanı katıştırılmış ifadede, aşağıdaki gibi yeniden bildirebilirsiniz:  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 Ancak, daha iyi bir yaklaşım genel varsayılan ad alanı kullanmak üzere daha kullanışsız budur. Genel varsayılan ad alanı ile ad alanlarını bildirme olmadan XML değişmez değerleri kullanabilirsiniz. Sonuçta elde edilen XML varsayılan genel olarak bildirilen ad alanında olacaktır.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a>XML özellikleri ile ad alanlarını kullanma  
 XML özellikleri de doğru ad alanında olması bir ad alanı içinde bir XML ağacı çalıştığınız ve XML özellikleri kullanırsanız, genel ad alanı kullanmanız gerekir. Aşağıdaki örnek, bir XML ad alanı ağacında bildirir. Ardından sayısını yazdırır `Child` öğeleri.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Bu örnek olduğunu gösteren hiçbir `Child` öğeleri. Şu çıkışı üretir:  
  
```  
0  
```  
  
 Ardından ancak, varsayılan genel ad alanı bildirirseniz değişmez değer XML ve XML özelliği varsayılan genel ad alanında şunlardır:  
  
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
  
 Bu örnek bir tane olduğunu gösteren `Child` öğesi. Şu çıkışı üretir:  
  
```  
1  
```  
  
 Bir ön ekine sahip genel bir ad alanı bildirirseniz XML değişmez değerleri ve XML özellikleri için önek kullanabilirsiniz:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)

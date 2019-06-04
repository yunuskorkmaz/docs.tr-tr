---
title: 'Nasıl yapılır: Boş sorgu sonucu kümelerinin hatalarını ayıklama (C#)'
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: ba82e37ef4f57c78e7ba66676ba90312c2a9400f
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485767"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Nasıl yapılır: Boş sorgu sonucu kümelerinin hatalarını ayıklama (C#)
XML ağaçlarını sorgulama sırasında sık karşılaşılan sorunlar XML ağacı varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanında geliştirici bazen sorgu yazdığını biridir.  
  
 Bu konudaki örnekler ilk kümesi, varsayılan ad alanı XML yüklenir ve hatalı sorgulanır normal bir şekilde gösterir.  
  
 XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.  
  
 Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanında XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Bu örnek aşağıdaki sonucu üretir:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu içinde XML oluşturulmasını gösterir.  
  
 Çözümüdür bildirmek ve başlatmak için bir <xref:System.Xml.Linq.XNamespace> nesnesi ve belirtirken kullanılacak <xref:System.Xml.Linq.XName> nesneleri. Bu durumda, bağımsız değişkeni <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi bir <xref:System.Xml.Linq.XName> nesne.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Bu örnek aşağıdaki sonucu üretir:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  

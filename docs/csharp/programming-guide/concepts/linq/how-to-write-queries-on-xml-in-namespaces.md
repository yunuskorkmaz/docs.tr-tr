---
title: Ad alanlarında XML'de sorgu yazma (C#)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337369"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Ad alanlarında XML'de sorgu yazma (C#)
XML'de ad alanında bir sorgu yazmak için <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri kullanmanız gerekir.  
  
 C# için en yaygın yaklaşım, URI <xref:System.Xml.Linq.XNamespace> içeren bir dize kullanarak bir başlangıç yapmak, ardından ad alanını yerel adla birleştirmek için ek işleci aşırı yüklenmesini kullanmaktır.  
  
 Bu konudaki ilk örnek kümesi, varsayılan ad alanında bir XML ağacının nasıl oluşturultur olduğunu gösterir. İkinci küme, bir ad alanında önek içeren bir XML ağacının nasıl oluşturultur olduğunu gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte varsayılan ad alanında bir XML ağacı oluşturulur. Daha sonra bir öğe koleksiyonu alır.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
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
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>Örnek  
 C#'da, önklü bir ad alanı kullanan bir XML ağacında veya varsayılan ad alanına sahip bir XML ağacında sorgu lar yazıp yazmadığınıza bakılmaksızın sorguları aynı şekilde yazarsınız.  
  
 Aşağıdaki örnek, önek içeren bir ad alanında olan bir XML ağacı oluşturur. Daha sonra bir öğe koleksiyonu alır.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İsim Alanlarına Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md)

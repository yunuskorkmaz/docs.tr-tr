---
title: 'Nasıl yapılır: Ad alanlarında XML üzerinde sorgu yazma (C#)'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: d33ecc22d8eb6ea4a08b56fbed6b6b437a5e3216
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484637"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Nasıl yapılır: Ad alanlarında XML üzerinde sorgu yazma (C#)
Bir ad alanındaki XML üzerinde sorgu yazmak için kullanmalısınız <xref:System.Xml.Linq.XName> doğru ad alanı olan nesne.  
  
 C# ' ta başlatmak için en yaygın bir yaklaşım olan bir <xref:System.Xml.Linq.XNamespace> URI içeren bir dize ardından kullanarak toplama işleci aşırı yükleme yerel adı ad alanı birleştirin.  
  
 Bu konudaki örnekler ilk kümesi, varsayılan ad alanında bir XML ağacı oluşturma işlemi gösterilmektedir. İkinci küme, önekli ad alanında bir XML ağacı oluşturma işlemi gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur. Ardından, öğelerinin bir koleksiyonunu alır.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Örnek  
 C# ' ta, sorguları olup bir ad alanı öneki ile kullanan bir XML ağacı veya varsayılan bir ad alanı ile XML ağacı sorguları yazıyorsanız bağımsız olarak aynı şekilde yazın.  
  
 Aşağıdaki örnek, bir ad alanı öneki olan bir XML ağacı oluşturur. Ardından, öğelerinin bir koleksiyonunu alır.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)

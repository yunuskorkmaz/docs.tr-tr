---
title: Ad alanlarında XML üzerinde sorgu yazma (C#)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337369"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Ad alanlarında XML üzerinde sorgu yazma (C#)
Bir ad alanında olan XML üzerinde bir sorgu yazmak için, doğru ad alanına sahip <xref:System.Xml.Linq.XName> nesneleri kullanmanız gerekir.  
  
 İçin C#en yaygın YAKLAŞıM, URI 'yi içeren bir dize kullanarak bir <xref:System.Xml.Linq.XNamespace> başlatmaktır ve sonra ad alanını yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanır.  
  
 Bu konudaki ilk örnek kümesi, varsayılan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir. İkinci küme, öneki olan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan bir ad alanında bulunan bir XML ağacı oluşturur. Daha sonra bir öğe koleksiyonu alır.  
  
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
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>Örnek  
 ' C#De, ön ek içeren bir ad alanı kullanan bir XML ağacına veya varsayılan bir ad alanına sahıp bir XML ağacına sorgu yazarken aynı şekilde sorgular yazarsınız.  
  
 Aşağıdaki örnek, öneki olan bir ad alanında olan bir XML ağacı oluşturur. Daha sonra bir öğe koleksiyonu alır.  
  
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
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md)

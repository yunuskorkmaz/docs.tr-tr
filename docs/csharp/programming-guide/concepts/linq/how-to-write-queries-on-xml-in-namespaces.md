---
title: Ad alanlarında XML üzerinde sorgu yazma (C#)
description: Ad alanlarında XML üzerinde sorgu yazmayı öğrenin. Bu sorgular için, doğru ad alanına sahip XName nesnelerini kullanmanız gerekir.
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303185"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Ad alanlarında XML üzerinde sorgu yazma (C#)
Bir ad alanında olan XML üzerinde bir sorgu yazmak için, <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri kullanmanız gerekir.  
  
 C# için en yaygın yaklaşım, <xref:System.Xml.Linq.XNamespace> URI 'yi içeren bir dize kullanarak başlatmak, ardından ad alanını yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanmaktır.  
  
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
 C# ' ta, ön ek içeren bir ad alanı kullanan bir XML ağacına veya varsayılan bir ad alanı olan bir XML ağacına sorgu yazarken aynı şekilde sorgular yazarsınız.  
  
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

- [Ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)

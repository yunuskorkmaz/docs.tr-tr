---
title: "Nasıl yapılır: XML ad alanları (C#) içinde sorguları yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 194e12f88f7c22c365a18bc2dd42a3dd26b5c569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Nasıl yapılır: XML ad alanları (C#) içinde sorguları yazma
İçinde bir ad alanı XML bir sorgu yazmak için kullanmanız gerekir <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri.  
  
 C# ' ta en yaygın başlatmak için yaklaşımdır bir <xref:System.Xml.Linq.XNamespace> URI içeren bir dize sonra kullanımı Toplama işleci aşırı ad alanı yerel ad ile birleştirmek için.  
  
 Bu konudaki örnekler ilk kümesi varsayılan ad alanında bir XML ağacı oluşturulacağını gösterir. İkinci küme öneki bir ad alanındaki bir XML ağacı oluşturulacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur. Ardından, öğe koleksiyonunu alır.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Örnek  
 C# ' ta, sorguları olup bir ad alanı öneki ile kullanan bir XML ağaç veya varsayılan ad alanını içeren bir XML ağacı sorguları yazıyorsanız bağımsız olarak aynı şekilde yazın.  
  
 Aşağıdaki örnek, bir ad alanı öneki bulunduğu bir XML ağacı oluşturur. Ardından, öğe koleksiyonunu alır.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)

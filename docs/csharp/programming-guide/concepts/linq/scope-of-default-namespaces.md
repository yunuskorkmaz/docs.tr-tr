---
title: C# Dilinde Varsayılan Ad Alanlarının Kapsamı
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253047"
---
# <a name="scope-of-default-namespaces-in-c"></a>C'deki Varsayılan Ad Alanlarının Kapsamı\#
XML ağacında temsil edilen varsayılan ad alanları sorgular için kapsam içinde değildir. Varsayılan ad alanında bulunan XML'niz varsa, yine <xref:System.Xml.Linq.XNamespace> de bir değişken ilbildirmeniz ve sorguda kullanılacak nitelikli bir ad yapmak için bunu yerel adla birleştirmeniz gerekir.  
  
 XML ağaçlarını sorgularken en sık karşılaşılan sorunlardan biri, XML ağacının varsayılan ad alanı varsa, geliştiricinin bazen sorguyu XML ad alanında değilmiş gibi yazmasıdır.  
  
 Bu konudaki ilk örnek kümesi, varsayılan ad alanında XML'nin yüklenmesinin tipik bir yolunu gösterir, ancak yanlış sorgulanır.  
  
 İkinci örnek kümesi, xml'i bir ad alanında sorgulayabilmeniz için gerekli düzeltmeleri gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanında XML oluşturulmasını ve boş bir sonuç kümesidöndüren bir sorguyu gösterir.  
  
### <a name="code"></a>Kod  
  
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
  
### <a name="comments"></a>Yorumlar  
 Bu örnek aşağıdaki sonucu üretir:  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanında XML oluşturulmasını ve düzgün kodlanmış bir sorguyu gösterir.  
  
 Yukarıdaki yanlış kodlanmış örneğin aksine, C# kullanırken doğru yaklaşım, bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirmek ve başlatmak <xref:System.Xml.Linq.XName> ve nesneleri belirtirken kullanmaktır. Bu durumda, yönteme <xref:System.Xml.Linq.XContainer.Elements%2A> bağımsız değişken <xref:System.Xml.Linq.XName> bir nesnedir.  
  
### <a name="code"></a>Kod  
  
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
  
### <a name="comments"></a>Yorumlar  
 Bu örnek aşağıdaki sonucu üretir:  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İsim Alanlarına Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md)

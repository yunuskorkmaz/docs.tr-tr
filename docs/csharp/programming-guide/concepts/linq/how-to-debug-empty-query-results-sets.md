---
title: Boş sorgu sonuç kümelerini hata ayıklama (C#)
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 2716f7c525ac6bee8d2fb374e4ecc4c975d852a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141285"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Boş sorgu sonuç kümelerini hata ayıklama (C#)
XML ağaçlarını sorgularken en sık karşılaşılan sorunlardan biri, XML ağacının varsayılan ad alanı varsa, geliştiricinin bazen sorguyu XML ad alanında değilmiş gibi yazmasıdır.  
  
 Bu konudaki ilk örnek kümesi, varsayılan ad alanında XML'nin yüklenmesinin ve yanlış sorgulanan tipik bir şekilde gösterir.  
  
 İkinci örnek kümesi, xml'i bir ad alanında sorgulayabilmeniz için gerekli düzeltmeleri gösterir.  
  
 Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanında XML oluşturulmasını ve boş bir sonuç kümesidöndüren bir sorgugösterir.  
  
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
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanında XML oluşturulmasını ve düzgün kodlanmış bir sorgugösterir.  
  
 Çözüm, bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirmek ve başlatmak ve <xref:System.Xml.Linq.XName> nesneleri belirtirken kullanmaktır. Bu durumda, yönteme <xref:System.Xml.Linq.XContainer.Elements%2A> bağımsız değişken <xref:System.Xml.Linq.XName> bir nesnedir.  
  
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
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  

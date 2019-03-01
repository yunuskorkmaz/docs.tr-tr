---
title: C# 1 varsayılan ad alanlarının kapsamı
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: dfc86e2e58eb936106807aba21b2953f52101cbc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979716"
---
# <a name="scope-of-default-namespaces-in-c"></a>C dilinde varsayılan ad alanlarının kapsamı\#
XML ağacı içinde gösterilen varsayılan ad alanı, sorgular için kapsamda değildir. Yine de belirtmesi gerekir, varsayılan bir ad alanı XML varsa, bir <xref:System.Xml.Linq.XNamespace> değişkeni, sorguda kullanılan bir tam adı yerel adı ile birleştirebilirsiniz.  
  
 XML ağaçlarını sorgulama sırasında sık karşılaşılan sorunlar XML ağacı varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanında geliştirici bazen sorgu yazdığını biridir.  
  
 Bu konudaki örnekler ilk kümesi XML varsayılan ad alanı içinde yüklenir, ancak yanlış sorgulanır normal bir şekilde gösterir.  
  
 XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanında XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.  
  
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
  
### <a name="comments"></a>Açıklamalar  
 Bu örnek aşağıdaki sonucu üretir:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu içinde XML oluşturulmasını gösterir.  
  
 Yukarıdaki yanlış kodlanmış örnek aksine, C# kullanırken doğru bildirmek ve başlatmak için yaklaşımdır bir <xref:System.Xml.Linq.XNamespace> nesnesi ve belirtirken kullanılacak <xref:System.Xml.Linq.XName> nesneleri. Bu durumda, bağımsız değişkeni <xref:System.Xml.Linq.XElement.Elements%2A> yöntemi bir <xref:System.Xml.Linq.XName> nesne.  
  
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
  
### <a name="comments"></a>Açıklamalar  
 Bu örnek aşağıdaki sonucu üretir:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)

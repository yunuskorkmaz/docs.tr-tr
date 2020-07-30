---
title: Bağlam temelinde öğeleri bulan bir sorgu yazma (C#)
description: Bağlam temelinde öğeleri bulan bir sorgu yazmayı öğrenin. Kod örneklerine bakın ve ek kaynakları görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 64f09a41c2c1d01b0be8f776461f9be9df9ecb5f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303198"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a>Bağlam temelinde öğeleri bulan bir sorgu yazma (C#)
Bazen, bağlamlarına göre öğeleri seçen bir sorgu yazmanız gerekebilir. Önceki veya sonraki eşdüzey öğelere göre filtrelemek isteyebilirsiniz. Alt veya üst öğe öğelerine göre filtrelemek isteyebilirsiniz.  
  
 Bunu, bir sorgu yazarak ve yan tümcesindeki sorgunun sonuçlarını kullanarak yapabilirsiniz `where` . İlk olarak null ile test etmeniz ve sonra değeri test etmeniz gerekiyorsa, bir yan tümce içinde sorgu yapmak daha uygundur `let` ve sonra sonuçları `where` yan tümce içinde kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `p` hemen arkasından bir öğesi olan tüm öğeleri seçer `ul` .  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 Bu kod şu çıkışı oluşturur:  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 Bu kod şu çıkışı oluşturur:  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>

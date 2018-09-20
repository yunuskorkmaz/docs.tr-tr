---
title: XML ağacından (C#) öğe, öznitelik ve düğümleri kaldırma
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 9ce63ce6a4ef75dedc788efca11e8dd2bdb471eb
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320480"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>XML ağacından (C#) öğe, öznitelik ve düğümleri kaldırma
Bir XML ağacına öğe, öznitelik ve düğümleri diğer türleri kaldırma değiştirebilirsiniz.  
  
 Tek bir öğe veya tek bir öznitelik, bir XML belgesinden kaldırma açıktır. Ancak, öğeler veya öznitelikleri koleksiyonları kaldırırken, ilk listesini bir koleksiyona depolanabildiği ve öğeler veya öznitelikleri listeden silin. En iyi yaklaşımdır <xref:System.Xml.Linq.Extensions.Remove%2A> bu sizin için yapacak genişletme yöntemi.  
  
 Bunu yapmak için ana nedeni, bir XML ağacından almak koleksiyonların çoğu ertelenmiş yürütme kullanarak veriyor, olmasıdır. Önce bunları bir liste olarak depolanabildiği değil veya uzantı yöntemlerini kullanmazsanız, belirli bir sınıf hataların karşılaşmak mümkündür. Daha fazla bilgi için [karma bildirim temelli kod/kesinliği kod hataları karışımı (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Aşağıdaki yöntemlerden bir XML ağacından düğümleri ve özniteliklerini kaldırın.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Kaldırır bir <xref:System.Xml.Linq.XAttribute> üst öğesinden.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Alt düğümleri kaldırır bir <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|İçerik kaldırır ve özniteliklerini bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Özniteliklerini kaldırır bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Geçirirseniz `null` değeri için ardından özniteliğini kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Geçirirseniz `null` değeri için ardından alt öğeyi kaldırır.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Kaldırır bir <xref:System.Xml.Linq.XNode> üst öğesinden.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Her bir öznitelik veya öğenin üst öğesi kaynak koleksiyondan kaldırır.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Bu örnekte, öğelerin kaldırılması için üç yaklaşım gösterilmektedir. İlk olarak, tek bir öğe kaldırır. İkinci olarak, öğelerinin bir koleksiyonunu alır, bunları gerçekleştiren kullanarak <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> işleci ve koleksiyon kaldırır. Son olarak, öğelerinin bir koleksiyonunu alır ve bunları kaldırır kullanarak <xref:System.Xml.Linq.Extensions.Remove%2A> genişletme yöntemi.  
  
 Daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> işleci bkz [veri türlerini dönüştürme (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).  
  
### <a name="code"></a>Kod  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
    <Child1>  
        <GrandChild1/>  
        <GrandChild2/>  
        <GrandChild3/>  
    </Child1>  
    <Child2>  
        <GrandChild4/>  
        <GrandChild5/>  
        <GrandChild6/>  
    </Child2>  
    <Child3>  
        <GrandChild7/>  
        <GrandChild8/>  
        <GrandChild9/>  
    </Child3>  
</Root>");  
root.Element("Child1").Element("GrandChild1").Remove();  
root.Element("Child2").Elements().ToList().Remove();  
root.Element("Child3").Elements().Remove();  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a>Açıklamalar  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 İlk en alt öğeyi kaldırılmıştır bildirimi `Child1`. Tüm alt bağımlı öğelere öğeleri kaldırılmış olan `Child2` ve `Child3`.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [(LINQ to XML) XML ağaçlarını değiştirme (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

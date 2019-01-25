---
title: (Visual Basic) XML ağacından öğe, öznitelik ve düğümleri kaldırma
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: eee761772d920c6f6fa49b3ddd8b3142ec9f5e43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495779"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>(Visual Basic) XML ağacından öğe, öznitelik ve düğümleri kaldırma
Bir XML ağacına öğe, öznitelik ve düğümleri diğer türleri kaldırma değiştirebilirsiniz.  
  
 Tek bir öğe veya tek bir öznitelik, bir XML belgesinden kaldırma açıktır. Ancak, öğeler veya öznitelikleri koleksiyonları kaldırırken, ilk listesini bir koleksiyona depolanabildiği ve öğeler veya öznitelikleri listeden silin. En iyi yaklaşımdır <xref:System.Xml.Linq.Extensions.Remove%2A> bu sizin için yapacak genişletme yöntemi.  
  
 Bunu yapmak için ana nedeni, bir XML ağacından almak koleksiyonların çoğu ertelenmiş yürütme kullanarak veriyor, olmasıdır. Önce bunları bir liste olarak depolanabildiği değil veya uzantı yöntemlerini kullanmazsanız, belirli bir sınıf hataların karşılaşmak mümkündür. Daha fazla bilgi için [karma bildirim temelli kod/kesinliği kod hataları karışımı (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
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
  
 Daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> işleci bkz [dönüştürme veri türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
### <a name="code"></a>Kod  
  
```vb  
Dim root As XElement = _  
    <Root>  
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
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [(LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

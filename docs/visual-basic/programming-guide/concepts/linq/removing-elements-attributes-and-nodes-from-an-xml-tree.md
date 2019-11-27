---
title: XML Ağacından Öğe, Öznitelik ve Düğümleri Kaldırma
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: 4cce1eff469c1f737e18b88cce30155547d9f11b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348948"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (Visual Basic)
Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.  
  
 Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir. Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz. En iyi yaklaşım, bunu sizin için yapacağız <xref:System.Xml.Linq.Extensions.Remove%2A> genişletme yöntemini kullanmaktır.  
  
 Bunu yapmanın asıl nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak yapılır. İlk olarak bunları bir liste içine almayın veya uzantı yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür. Daha fazla bilgi için bkz. [karma bildirim kodu/tanımlayıcı kod hataları (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XAttribute> üst öğesinden kaldırır.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Bir <xref:System.Xml.Linq.XContainer>alt düğümleri kaldırır.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XElement>içeriği ve öznitelikleri kaldırır.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XElement>özniteliklerini kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Değer için `null` geçirirseniz, özniteliğini kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Değer için `null` geçirirseniz, alt öğeyi kaldırır.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XNode> üst öğesinden kaldırır.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırır.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir. İlk olarak, tek bir öğeyi kaldırır. İkincisi, bir öğe koleksiyonunu alır, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> işlecini kullanarak bunları çıkarır ve koleksiyonu kaldırır. Son olarak, bir öğe koleksiyonunu alır ve <xref:System.Xml.Linq.Extensions.Remove%2A> Extension metodunu kullanarak onları kaldırır.  
  
 <xref:System.Linq.Enumerable.ToList%2A> işleci hakkında daha fazla bilgi için bkz. [veri türlerini dönüştürme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
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
  
 İlk alt öğenin `Child1`kaldırıldığına dikkat edin. Tüm alt öğe öğeleri `Child2` ve `Child3`öğesinden kaldırılmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

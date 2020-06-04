---
title: XML Ağacından Öğe, Öznitelik ve Düğümleri Kaldırma
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: f8be7fe521fb3c2662b105e34fd96fea1d1ac6e7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413419"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (Visual Basic)
Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.  
  
 Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir. Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz. En iyi yaklaşım, bunu <xref:System.Xml.Linq.Extensions.Remove%2A> sizin için sağlayacak olan genişletme yöntemini kullanmaktır.  
  
 Bunu yapmanın asıl nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak yapılır. İlk olarak bunları bir liste içine almayın veya uzantı yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür. Daha fazla bilgi için bkz. [karma bildirim kodu/tanımlayıcı kod hataları (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Bir öğesini <xref:System.Xml.Linq.XAttribute> üst öğesinden kaldırır.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Alt düğümleri bir öğesinden kaldırır <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Öğesinden içerik ve öznitelikleri kaldırır <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|, Özniteliklerini kaldırır <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|`null`Değerini geçirirseniz, özniteliğini kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|`null`Değer ' i geçirirseniz, alt öğeyi kaldırır.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Bir öğesini <xref:System.Xml.Linq.XNode> üst öğesinden kaldırır.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırır.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir. İlk olarak, tek bir öğeyi kaldırır. İkincisi, bir öğe koleksiyonunu alır, bunları işlecini kullanarak bunları <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> çıkarır ve koleksiyonu kaldırır. Son olarak, bir öğe koleksiyonunu alır ve genişletme yöntemini kullanarak onları kaldırır <xref:System.Xml.Linq.Extensions.Remove%2A> .  
  
 İşleci hakkında daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> bkz. [veri türlerini dönüştürme (Visual Basic)](converting-data-types.md).  
  
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
  
### <a name="comments"></a>Yorumlar  
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
  
 İlk alt öğenin öğesinden çıkarıldığına dikkat edin `Child1` . Tüm alt öğeler öğeleri öğesinden `Child2` ve kaynağından kaldırılmıştır `Child3` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)

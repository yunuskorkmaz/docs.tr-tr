---
title: Bir XML ağacına (Visual Basic) öğeleri, öznitelikleri ve düğümler ekleme
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 86d28f5974e30a9b7f1a1e830cd40c3cd916e8ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643019"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>Bir XML ağacına (Visual Basic) öğeleri, öznitelikleri ve düğümler ekleme
Varolan bir XML ağacına içerik (öğeleri, öznitelikleri, yorumlar, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.  
  
## <a name="methods-for-adding-content"></a>İçerik ekleme yöntemleri  
 Alt içerik için aşağıdaki yöntemleri ekleyin bir <xref:System.Xml.Linq.XElement> veya bir <xref:System.Xml.Linq.XDocument>:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|İçeriği, içerik alt sonuna ekler <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Alt öğe içeriğini başında içeriği ekler <xref:System.Xml.Linq.XContainer>.|  
  
 Aşağıdaki yöntemlerden içeriği eş düğümleri olarak eklemek bir <xref:System.Xml.Linq.XNode>. Eşdüzey içeriğin için eklediğiniz en yaygın düğüm <xref:System.Xml.Linq.XElement>, geçerli eşdüzey içeriği gibi diğer tür düğüm ekleyebilirsiniz, ancak <xref:System.Xml.Linq.XText> veya <xref:System.Xml.Linq.XComment>.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Sonra içerik ekler <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Önce içeriği ekler <xref:System.Xml.Linq.XNode>.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, iki XML ağaçları oluşturur ve ağaçları birini değiştirir.  
  
### <a name="code"></a>Kod  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
```  
  
### <a name="comments"></a>Açıklamalar  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ağaçları (LINQ-XML) değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

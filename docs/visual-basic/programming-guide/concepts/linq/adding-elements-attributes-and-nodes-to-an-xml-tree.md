---
title: XML Ağacına Öğe, Öznitelik ve Düğümler Ekleme
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 8d3d3a27194bb022434f09778dbf3960bd0b9853
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345820"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>XML ağacına öğe, öznitelik ve düğüm ekleme (Visual Basic)
Mevcut bir XML ağacına içerik (öğe, öznitelik, yorum, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.  
  
## <a name="methods-for-adding-content"></a>Içerik ekleme yöntemleri  
 Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>alt içerik ekler:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<xref:System.Xml.Linq.XContainer>alt içeriğinin sonuna içerik ekler.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<xref:System.Xml.Linq.XContainer>alt içeriğinin başlangıcında içerik ekler.|  
  
 Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XNode>eşdüzey düğümleri olarak içerik ekler. Eşdüzey içerik eklediğiniz en yaygın düğüm <xref:System.Xml.Linq.XElement>, ancak <xref:System.Xml.Linq.XText> veya <xref:System.Xml.Linq.XComment>gibi diğer düğüm türlerine geçerli eşdüzey içerik ekleyebilirsiniz.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<xref:System.Xml.Linq.XNode>sonra içerik ekler.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<xref:System.Xml.Linq.XNode>öncesine içerik ekler.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek iki XML ağacı oluşturur ve sonra ağaçlardan birini değiştirir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

---
title: XML Ağacına Öğe, Öznitelik ve Düğümler Ekleme
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 5b80a19c952388c2591536077f382df2f69fe80f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383903"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>XML ağacına öğe, öznitelik ve düğüm ekleme (Visual Basic)
Mevcut bir XML ağacına içerik (öğe, öznitelik, yorum, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.  
  
## <a name="methods-for-adding-content"></a>Içerik ekleme yöntemleri  
 Aşağıdaki yöntemler bir veya öğesine alt içerik ekler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> :  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Öğesinin alt içeriğinin sonuna içerik ekler <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Öğesinin alt içeriğinin başlangıcına içerik ekler <xref:System.Xml.Linq.XContainer> .|  
  
 Aşağıdaki yöntemler bir öğesinin eşdüzey düğümleri olarak içerik ekler <xref:System.Xml.Linq.XNode> . Eşdüzey içerik eklediğiniz en yaygın düğüm, <xref:System.Xml.Linq.XElement> veya gibi diğer düğüm türlerine geçerli eşdüzey içerik eklemenize olanak sağlar <xref:System.Xml.Linq.XText> <xref:System.Xml.Linq.XComment> .  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Öğesinden sonra içerik ekler <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Öğesinden önce içerik ekler <xref:System.Xml.Linq.XNode> .|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
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
  
### <a name="comments"></a>Yorumlar  
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

- [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)

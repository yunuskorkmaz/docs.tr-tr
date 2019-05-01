---
title: Görsel Basic2 XML değişmez değerlerine giriş
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 68ba1e018d4ad9501532745a88090f0f756b5c17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61834281"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Visual Basic'de XML değişmez değerlerine giriş
Bu bölümde, Visual Basic'te XML ağaçları oluşturma hakkında bilgi sağlar.  
  
 LINQ sorguları sonuçları içerik olarak bir XML ağacı için kullanma hakkında daha fazla bilgi için bkz: [işlevsel oluşturma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Visual Basic'de XML değişmez değerleri hakkında daha fazla bilgi için bkz. [XML Visual Basic'te LINQ genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>XML Ağaçları Oluşturma  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Xml.Linq.XElement>, bu durumda `contacts`:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a>Bir XElement ile basit içerik oluşturma  
 Oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> basit içerik aşağıdaki gibi içerir:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Boş bir öğe oluşturma  
 Boş bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement>gibi:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Katıştırılmış ifadeler kullanma  
 XML değişmez değerlerini ve önemli bir özelliği, katıştırılmış ifadeler sağlarlar ' dir. Katıştırılmış ifadeler bir ifadeyi değerlendirir ve sonuçları XML ağacına eklemek etkinleştirin. İfade için bir tür olarak değerlendirilirse <xref:System.Xml.Linq.XElement>, öğenin ağacına eklenir. İfade için bir tür olarak değerlendirilirse <xref:System.Xml.Linq.XAttribute>, bir öznitelik ağacına eklenir. Yalnızca geçerli olduğu yerlerde ağacına öğeler ve öznitelikler ekleyebilirsiniz.  
  
 Tek bir ifade yalnızca katıştırılmış bir ifadeyi gidebilirsiniz dikkat edin önemlidir. Birden çok deyime katıştırılamıyor. Bir ifade tek bir satır geçerse, satır devamı karakteri kullanmanız gerekir.  
  
 Var olan düğümleri (öğeler dahil) ve yeni bir XML ağacı öznitelikleri ve var olan düğümleri zaten shapemap varsa eklemek için bir katıştırılmış deyim kullanırsanız, düğüm klonlanır. Yeni kopyalanan düğümleri yeni XML ağacına eklenir. Var olan düğümleri arasındaki shapemap değil, düğümler yalnızca yeni XML ağacına eklenir. Bu konu Son örnekte bu gösterir.  
  
 Aşağıdaki örnek, katıştırılmış bir ifade ağacına bir öğe eklemek için kullanır:  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>İçerik için katıştırılmış ifadeleri kullanma  
 Bir öğenin içeriğini sağlamak için katıştırılmış bir ifade kullanabilirsiniz:  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Katıştırılmış bir ifadede bir LINQ Sorgu kullanma  
 Bir öğenin içeriğini bir LINQ sorgusunun sonuçları kullanabilirsiniz:  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>Düğüm adları için katıştırılmış ifadeleri kullanma  
 Katıştırılmış ifadeler, öznitelik adları, öznitelik değerleri, öğe adları ve değerleri hesaplamak için de kullanabilirsiniz:  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>Kopyalama ve Ekleme Karşılaştırması  
 Var olan düğümleri arasındaki shapemap zaten varsa var olan düğümleri (öğeler dahil) ve öznitelikler yeni bir XML ağacına eklemek için bir katıştırılmış deyim kullanırsanız, daha önce belirtildiği gibi düğümler kopyalanır ve yeni kopyalanan düğümleri yeni XML ağacına eklenir. Var olan düğümleri arasındaki shapemap değil, bunlar yalnızca yeni XML ağacına eklenir.  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

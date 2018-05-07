---
title: XML değişmez değerlerine Visual Basic2 giriş
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: bac0a4a297dcecce5465e5a1a1c02e4cbc9848a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Visual Basic'de XML değişmez değerleri giriş
Bu bölümde, Visual Basic'te XML ağaçları oluşturma hakkında bilgi sağlar.  
  
 LINQ sorgularını sonuçlarını içerik için bir XML ağacı kullanma hakkında daha fazla bilgi için bkz: [işlevsel yapımı (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Visual Basic'de XML değişmez değerleri hakkında daha fazla bilgi için bkz: [XML Visual Basic'te LINQ genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>XML ağaçları oluşturma  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Xml.Linq.XElement>, bu durumda `contacts`:  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>Basit içerikle bir XElement oluşturma  
 Oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> basit içerik, aşağıdaki gibi içeren:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Boş bir öğe oluşturma  
 Boş bir oluşturabileceğiniz <xref:System.Xml.Linq.XElement>aşağıdaki gibi:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Katıştırılmış ifadeler kullanma  
 Katıştırılmış ifadeler izin XML değişmez değerleri, önemli özelliklerinden biridir. Katıştırılmış ifadeler bir ifade değerlendirme ve ifade sonuçlarını XML ağacına eklemek etkinleştirin. İfade türü için değerlendirilirse <xref:System.Xml.Linq.XElement>, bir öğenin ağacına eklenir. İfade türü için değerlendirilirse <xref:System.Xml.Linq.XAttribute>, bir öznitelik ağacına eklenir. Yalnızca geçerli olduğu yerlerde ağacına öğeleri ve özniteliklerinin ekleyebilirsiniz.  
  
 Yalnızca tek bir ifade katıştırılmış bir ifadeyi gidebilirsiniz dikkate almak önemlidir. Birden çok deyime eklenemiyor. Bir ifade tek bir satır geçerse, satır devamlılığı karakteri kullanmanız gerekir.  
  
 (Öğeleri dahil) varolan düğümleri ve yeni bir XML ağacı öznitelikleri ve varolan düğümleri zaten üst öğe varsa eklemek için katıştırılmış bir ifade kullanırsanız, düğüm kopyalandığı. Yeni kopyalanmış düğümleri yeni XML ağacına eklenir. Varolan düğümleri üst öğe değil, düğümleri yalnızca yeni bir XML ağacı bağlanmış. Bu konudaki son örnek bu gösterir.  
  
 Aşağıdaki örnek katıştırılmış bir ifade ağacına bir öğe eklemek için kullanır:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>İçerik için katıştırılmış ifadeler kullanma  
 Katıştırılmış bir ifade, bir öğenin içeriğini sağlamak için kullanabilirsiniz:  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Katıştırılmış bir ifadede bir LINQ Sorgu kullanma  
 Bir öğenin içeriğini için bir LINQ Sorgu sonucunu kullanabilirsiniz:  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>Katıştırılmış ifadeler için düğüm adlarını kullanma  
 Katıştırılmış ifadeler, öznitelik adları, öznitelik değerleri, öğe adları ve öğe değerleri hesaplamak için de kullanabilirsiniz:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>Kopyalama vs. Ekleme  
 Varolan düğümleri üst öğe zaten varsa yeni bir XML ağacına (öğeleri dahil) varolan düğümleri ve öznitelikler eklemek için katıştırılmış bir ifade kullanırsanız, daha önce belirtildiği gibi düğümleri kopyalandığı ve yeni kopyalanmış düğümleri yeni XML ağacına bağlı. Varolan düğümleri üst öğe değil, yalnızca yeni bir XML ağacı eklenir.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

---
title: Visual Basic2'de XML Literals'e Giriş2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 9f5c54574e51c537d9ea58d307afda10736d0d88
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266956"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Visual Basic'te XML Literals'e Giriş
Bu bölümde Visual Basic'te XML ağaçları oluşturma hakkında bilgi verilmektedir.  
  
 BIR XML ağacının içeriği olarak LINQ sorgularının sonuçlarını kullanma hakkında bilgi [için](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)bkz.  
  
 Visual Basic'teki XML literalleri hakkında daha fazla bilgi için [Visual Basic'te LINQ'dan XML'e Genel Bakış bölümüne](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)bakın.  
  
## <a name="creating-xml-trees"></a>XML Ağaçları Oluşturma  
 Aşağıdaki örnek, bu durumda <xref:System.Xml.Linq.XElement> `contacts`nasıl oluşturulacak gösterir:  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>Basit İçerikli XElement Oluşturma  
 Aşağıdaki gibi <xref:System.Xml.Linq.XElement> basit içerik içeren bir oluşturabilirsiniz:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Boş Öğe Oluşturma  
 Aşağıdaki gibi boş <xref:System.Xml.Linq.XElement>bir oluşturabilirsiniz:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Gömülü İfadeleri Kullanma  
 XML literals önemli bir özelliği gömülü ifadeler izin olmasıdır. Katıştılmış ifadeler, bir ifadeyi değerlendirmenize ve ifadenin sonuçlarını XML ağacına eklemenize olanak tanır. İfade bir <xref:System.Xml.Linq.XElement>tür, öğe ağaca eklenir değerlendirirse. İfade bir <xref:System.Xml.Linq.XAttribute>tür, bir öznitelik ağaca eklenir değerlendirirse. Öğeleri ve öznitelikleri yalnızca geçerli oldukları ağaca ekleyebilirsiniz.  
  
 Yalnızca tek bir ifadenin katıştırılmış bir ifadeye girebileceğini unutmayın. Birden çok deyim katıştıramazsınız. Bir ifade tek bir satırın ötesine uzanıyorsa, satır devam karakterini kullanmanız gerekir.  
  
 Yeni bir XML ağacına varolan düğümleri (öğeler dahil) ve öznitelikleri eklemek için katıştırılmış bir ifade kullanırsanız ve varolan düğümler zaten ebeveynlik varsa, düğümler klonlanır. Yeni klonlanan düğümler yeni XML ağacına eklenir. Varolan düğümler ebeveynli değilse, düğümler yalnızca yeni XML ağacına eklenir. Bu konudaki son örnek bunu göstermektedir.  
  
 Aşağıdaki örnek, ağaca bir öğe eklemek için katışlı bir ifade kullanır:  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>İçerik için Gömülü İfadeleri Kullanma  
 Bir öğenin içeriğini sağlamak için katıştırılmış bir ifade kullanabilirsiniz:  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Gömülü İfadede LINQ Sorgusu Kullanma  
 Bir öğenin içeriği için LINQ sorgusunun sonuçlarını kullanabilirsiniz:  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>Düğüm Adları için Gömülü İfadeleri Kullanma  
 Öznitelik adlarını, öznitelik değerlerini, öğe adlarını ve öğe değerlerini hesaplamak için közlediğiniz ifadeleri de kullanabilirsiniz:  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>Klonlama ve Takma  
 Daha önce de belirtildiği gibi, varolan düğümleri (öğeler dahil) ve yeni bir XML ağacına öznitelikleri eklemek için katıştırılmış bir ifade kullanırsanız, varolan düğümler zaten ebeveynlik varsa, düğümler klonlanır ve yeni klonlanan düğümler yeni XML ağacına eklenir. Varolan düğümler ebeveynli değilse, yalnızca yeni XML ağacına eklenir.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Ağaçları Oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

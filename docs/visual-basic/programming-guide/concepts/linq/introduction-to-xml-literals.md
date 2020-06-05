---
title: Visual Basic2 'de XML değişmez değerlerine giriş
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 8b92d22727c50274d57a5e407a0ca42807de3a94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397590"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Visual Basic XML değişmez değerlerine giriş
Bu bölüm, Visual Basic XML ağaçları oluşturma hakkında bilgi sağlar.  
  
 XML ağacının içeriği olarak LINQ sorgularının sonuçlarını kullanma hakkında daha fazla bilgi için bkz. [Işlevsel oluşturma (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).  
  
 Visual Basic XML değişmez değerleri hakkında daha fazla bilgi için bkz. [Visual Basic LINQ to XML genel bakış](../../language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>XML Ağaçları Oluşturma  
 Aşağıdaki örnek, bu durumda nasıl oluşturulacağını gösterir <xref:System.Xml.Linq.XElement> `contacts` :  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>Basit Içerikle XElement oluşturma  
 <xref:System.Xml.Linq.XElement>Basit içerik içeren bir oluşturmak için aşağıdaki gibi:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Boş bir öğe oluşturma  
 Şu şekilde boş bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement> :  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Katıştırılmış Ifadeler kullanma  
 XML sabit değerlerinin önemli bir özelliği, katıştırılmış ifadelere izin verleridir. Katıştırılmış ifadeler bir ifadeyi değerlendirmenizi ve ifadenin sonuçlarını XML ağacına eklemeyi sağlar. İfade bir türü olarak değerlendirilirse <xref:System.Xml.Linq.XElement> , ağaca bir öğe eklenir. İfade bir türü olarak değerlendirilirse <xref:System.Xml.Linq.XAttribute> , ağaca bir öznitelik eklenir. Öğeleri ve öznitelikleri yalnızca geçerli oldukları yerde ağaca ekleyebilirsiniz.  
  
 Yalnızca tek bir ifadenin katıştırılmış ifadeye gidebileceğini unutmayın. Birden çok deyimi katıştıramazsınız. Bir ifade tek bir çizgiyi aşarsa, satır devamlılık karakterini kullanmanız gerekir.  
  
 Varolan düğümleri (öğeler dahil) ve özniteliklerini yeni bir XML ağacına eklemek için katıştırılmış bir ifade kullanırsanız ve mevcut düğümlerin zaten üst öğesi varsa, düğümler klonlanır. Yeni kopyalanan düğümler yeni XML ağacına eklenir. Mevcut düğümler üst öğe değilse, düğümler yalnızca yeni XML ağacına eklenir. Bu konudaki son örnekte bu gösterilmektedir.  
  
 Aşağıdaki örnek, ağaca bir öğe eklemek için gömülü bir ifade kullanır:  
  
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
  
### <a name="using-embedded-expressions-for-content"></a>Içerik için katıştırılmış Ifadeler kullanma  
 Bir öğenin içeriğini sağlamak için gömülü bir ifade kullanabilirsiniz:  
  
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
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Katıştırılmış Ifadede LINQ sorgusu kullanma  
 Bir öğenin içeriği için LINQ sorgusunun sonuçlarını kullanabilirsiniz:  
  
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
  
### <a name="using-embedded-expressions-for-node-names"></a>Düğüm adları için katıştırılmış Ifadeler kullanma  
 Öznitelik adlarını, öznitelik değerlerini, öğe adlarını ve öğe değerlerini hesaplamak için katıştırılmış ifadeler de kullanabilirsiniz:  
  
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
 Daha önce belirtildiği gibi, var olan düğümleri (öğeler dahil) ve özniteliklerini yeni bir XML ağacına eklemek için katıştırılmış bir ifade kullanırsanız, varolan düğümlerin zaten üst öğesi varsa, düğümler kopyalanır ve yeni kopyalanan düğümler yeni XML ağacına eklenir. Mevcut düğümler üst öğe değilse, bunlar yalnızca yeni XML ağacına eklenir.  
  
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
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları oluşturma (Visual Basic)](creating-xml-trees.md)

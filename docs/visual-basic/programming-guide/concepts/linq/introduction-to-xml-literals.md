---
title: Visual Basic2 'de XML değişmez değerlerine giriş
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 5355a3c0f01bb247e38e52816693ee47d7d50556
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834987"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Visual Basic XML değişmez değerlerine giriş
Bu bölüm, Visual Basic XML ağaçları oluşturma hakkında bilgi sağlar.  
  
 XML ağacının içeriği olarak LINQ sorgularının sonuçlarını kullanma hakkında daha fazla bilgi için bkz. [Işlevsel oluşturma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Visual Basic XML değişmez değerleri hakkında daha fazla bilgi için bkz. [Visual Basic LINQ to XML genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>XML ağaçları oluşturma  
 Aşağıdaki örnek, bu durumda <xref:System.Xml.Linq.XElement> `contacts` ' in nasıl oluşturulacağını gösterir:  
  
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
 Basit içerik içeren <xref:System.Xml.Linq.XElement> ' ı aşağıdaki gibi oluşturabilirsiniz:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Boş bir öğe oluşturma  
 Boş bir <xref:System.Xml.Linq.XElement>, aşağıdaki gibi oluşturabilirsiniz:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Katıştırılmış Ifadeler kullanma  
 XML sabit değerlerinin önemli bir özelliği, katıştırılmış ifadelere izin verleridir. Katıştırılmış ifadeler bir ifadeyi değerlendirmenizi ve ifadenin sonuçlarını XML ağacına eklemeyi sağlar. İfade <xref:System.Xml.Linq.XElement> türü olarak değerlendirilirse, ağaca bir öğe eklenir. İfade <xref:System.Xml.Linq.XAttribute> türü olarak değerlendirilirse, ağaca bir öznitelik eklenir. Öğeleri ve öznitelikleri yalnızca geçerli oldukları yerde ağaca ekleyebilirsiniz.  
  
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
  
### <a name="cloning-vs-attaching"></a>Kopyalama ve Iliştirme  
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

- [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

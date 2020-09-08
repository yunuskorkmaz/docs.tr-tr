---
title: Visual Basic XML sabit değerleri LINQ to XML
description: XML sabit değerlerini ve katıştırılmış ifadeleri kullanarak Visual Basic bir XML ağacı oluşturabilirsiniz. Katıştırılmış ifadeler bir ifadeyi değerlendirmenizi ve ifadenin sonuçlarını XML ağacına eklemeyi sağlar.
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553206"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a>Visual Basic XML değişmez değerleri (LINQ to XML)

Bu makalede, XML sabit değerleri ve katıştırılmış ifadeler kullanılarak Visual Basic XML ağaçları oluşturma hakkında bilgi sağlanır.

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a>Örnek: XML ağacı oluşturmak için XML değişmez değerlerini kullanma

Aşağıdaki örnek, <xref:System.Xml.Linq.XElement> Bu örnekte `contacts` XML değişmez değerleri ile nasıl oluşturulacağını gösterir:

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

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a>Örnek: basit içerikli bir XElement oluşturmak için XML değişmez değerlerini kullanın

<xref:System.Xml.Linq.XElement>Basit içerik içeren bir oluşturmak için aşağıdaki gibi:

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a>Örnek: boş bir öğe oluşturmak için bir XML sabit değeri kullanın

Şu şekilde boş bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement> :

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a>İçerik oluşturmak için katıştırılmış ifadeleri kullanma

XML sabit değerlerinin önemli bir özelliği, katıştırılmış ifadelere izin verleridir. Katıştırılmış ifadeler bir ifadeyi değerlendirmenizi ve ifadenin sonuçlarını XML ağacına eklemeyi sağlar. İfade bir türü olarak değerlendirilirse <xref:System.Xml.Linq.XElement> , ağaca bir öğe eklenir. İfade bir türü olarak değerlendirilirse <xref:System.Xml.Linq.XAttribute> , ağaca bir öznitelik eklenir. Öğeleri ve öznitelikleri yalnızca geçerli oldukları yerde ağaca ekleyebilirsiniz.

yalnızca tek bir ifadenin katıştırılmış ifadeye gidebileceğini unutmayın. Birden çok deyimi katıştıramazsınız. Bir ifade tek bir çizgiyi aşarsa, satır devamlılık karakterini kullanmanız gerekir.

Varolan düğümleri (öğeler dahil) ve özniteliklerini yeni bir XML ağacına eklemek için katıştırılmış bir ifade kullanırsanız ve mevcut düğümlerin zaten üst öğesi varsa, düğümler klonlanır. Yeni kopyalanan düğümler yeni XML ağacına eklenir. Mevcut düğümlerin üst öğesi yoksa, düğümler yalnızca yeni XML ağacına eklenir. Bu makaledeki Son örnekte bu gösterilmektedir.

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a>Örnek: bir öğe eklemek için gömülü bir ifade kullanın

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

## <a name="example-use-an-embedded-expression-for-content"></a>Örnek: içerik için gömülü bir ifade kullanın

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

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a>Örnek: katıştırılmış ifadede LINQ sorgusu kullanma

Bir LINQ sorgusunun sonuçlarını bir öğenin içeriğini sağlamak için kullanabilirsiniz:

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

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a>Örnek: düğüm adları sağlamak için gömülü bir ifade kullanın

Ayrıca, öznitelik adlarını, öznitelik değerlerini, öğe adlarını ve öğe değerlerini hesaplamak için gömülü bir ifade kullanabilirsiniz:

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

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a>Örnek: düğümleri kopyalamak ve eklemek için gömülü bir ifade kullanın

Daha önce belirtildiği gibi, var olan düğümleri (öğeler dahil) ve özniteliklerini yeni bir XML ağacına eklemek için katıştırılmış bir ifade kullanırsanız ve eklenen düğümlerin düğümleri zaten üst öğe ise, düğümler kopyalanır ve kopyalar yeni XML ağacına eklenir. Mevcut düğümler üst öğe değilse, yeni XML ağacına eklenir.

Aşağıdaki kod, bir ağaca bir üst öğeye sahip bir öğe eklediğinizde ve bir ağaca üst öğesi olmayan bir öğe eklediğinizde davranışını gösterir.

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
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

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevsel oluşturma](functional-construction.md)

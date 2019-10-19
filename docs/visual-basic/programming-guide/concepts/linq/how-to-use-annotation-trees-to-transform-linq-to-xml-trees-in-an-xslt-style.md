---
title: 'Nasıl yapılır: XSLT stilinde LINQ to XML ağaçlarını dönüştürmek için ek açıklamaları kullanma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: b8f15c4dc6016e48619d26e7cc8717a2a3c5acd5
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581986"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a>Nasıl yapılır: XSLT stilinde LINQ to XML ağaçlarını dönüştürmek için ek açıklamaları kullanma (Visual Basic)

Ek açıklamalar, bir XML ağacının dönüştürmelerini kolaylaştırmak için kullanılabilir.

Bazı XML belgeleri "karışık içerikli belge merkezli" dir. Bu tür belgeler sayesinde bir öğenin alt düğümlerinin şeklini bilmeniz gerekmez. Örneğin, metin içeren bir düğüm şöyle görünebilir:

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

Herhangi bir metin düğümü için herhangi bir sayıda alt `<b>` ve `<i>` öğe olabilir. Bu yaklaşım birkaç farklı durum sağlar: gibi, normal paragraflar, madde işaretli paragraflar ve bit eşlemler gibi çeşitli alt öğeler içerebilen sayfalar. Bir tablodaki hücreler metin, açılan liste veya bit eşlemler içerebilir. Belge merkezli XML 'in birincil özelliklerinden biri, belirli bir öğenin hangi alt öğesi olacağını bilemezsiniz.

Dönüştürmek istediğiniz öğelerin alt öğeleri hakkında daha fazla bilgi sahibi olmadığınız bir ağaçtaki öğeleri dönüştürmek istiyorsanız, ek açıklamaları kullanan bu yaklaşım etkili bir yaklaşımdır.

Yaklaşımın Özeti:

- İlk olarak, ağaç içindeki öğeleri bir değiştirme öğesiyle birlikte not edin.

- İkinci olarak, tüm ağaç üzerinde yineleme yapın, her öğeyi ek açıklamasına göre değiştirdiğiniz yeni bir ağaç oluşturun. Bu örnek, `XForm` adlı bir işlevde yeni ağacın yinelemesini ve oluşturulmasını uygular.

Ayrıntılı olarak yaklaşım aşağıdakilerden oluşur:

- Bir şekilden diğerine dönüştürmek istediğiniz öğe kümesini döndüren bir veya daha fazla LINQ to XML sorgu yürütün. Sorgudaki her öğe için, öğeye ek açıklama olarak yeni bir <xref:System.Xml.Linq.XElement> nesnesi ekleyin. Bu yeni öğe, yeni, dönüştürülmüş ağaçtaki açıklamalı öğenin yerini alır. Bu, örnekte gösterildiği gibi yazılacak basit koddur.

- Ek açıklama olarak eklenen yeni öğe, yeni alt düğümler içerebilir; istediğiniz herhangi bir şekle sahip bir alt ağaç oluşturabilir.

- Özel bir kural var: yeni öğenin bir alt düğümü, bu amaçla oluşturulan bir ad alanı, farklı bir ad alanında ise (Bu örnekte, ad alanı `http://www.microsoft.com/LinqToXmlTransform/2007`), bu alt öğe yeni ağaca kopyalanmaz. Bunun yerine, ad alanı yukarıda belirtilen özel ad alanıdır ve öğenin yerel adı `ApplyTransforms` ise, Kaynak ağacındaki öğenin alt düğümleri yinelenir ve yeni ağaca kopyalanır (ek açıklamalı alt öğelerin olduğu özel durum ile). kendileri bu kurallara göre dönüştürülür).

- Bu, XSL 'teki dönüşümler belirtimine benzer. Düğüm kümesi seçen sorgu, bir şablon için XPath ifadesine benzer. Ek açıklama olarak kaydedilen yeni <xref:System.Xml.Linq.XElement> oluşturma kodu, XSL 'deki dizi oluşturucusuna benzerdir ve `ApplyTransforms` öğesi, XSL içindeki `xsl:apply-templates` öğesine benzerdir.

- Bu yaklaşımı almanın avantajlarından biri olan sorgular, her zaman değiştirilmemiş kaynak ağacına sorgu yazırsınız. Ağaçta yapılan değişikliklerin yazmakta olduğunuz sorguları nasıl etkilediği konusunda endişelenmeniz gerekmez.

## <a name="transforming-a-tree"></a>Ağacı dönüştürme

Bu ilk örnek, tüm `Paragraph` düğümlerini `para` olarak yeniden adlandırır:

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>
                <Paragraph>More text.</Paragraph>
            </Root>

        ' Replace Paragraph with p.
        For Each el In root...<Paragraph>
            ' same idea as xsl:apply-templates
            el.AddAnnotation( _
                <para>
                    <<%= at %>></>
                </para>)
        Next

        ' The XForm function, shown later in this topic, accomplishes the transform
        Dim newRoot As XElement = XForm(root)
        Console.WriteLine(newRoot)
    End Sub
End Module
```

 Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>
  <para>More text.</para>
</Root>
```

## <a name="a-more-complicated-transform"></a>Daha karmaşık bir dönüşüm

Aşağıdaki örnek, ağacı sorgular ve `Data` öğelerinin ortalamasını ve toplamını hesaplar ve bunları ağaca yeni öğeler olarak ekler.

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim data As XElement = _
            <Root>
                <Data>20</Data>
                <Data>10</Data>
                <Data>3</Data>
            </Root>

        ' While adding annotations, you can query the source tree all you want,
        ' as the tree is not mutated while annotating.
        data.AddAnnotation( _
            <Root>
                <<%= at %>/>
                <Average>
                    <%= _
                        String.Format("{0:F4}", _
                        data.Elements("Data") _
                        .Select(Function(z) CDec(z)).Average()) _
                    %>
                </Average>
                <Sum>
                    <%= _
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _
                    %>
                </Sum>
            </Root> _
        )

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(data)
        Console.WriteLine(vbNewLine)

        ' The XForm function, shown later in this topic, accomplishes the transform
        Dim newData As XElement = XForm(data)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newData)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```console
Before Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
</Root>

After Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
  <Average>11.0000</Average>
  <Sum>33</Sum>
</Root>
```

## <a name="effecting-the-transform"></a>Dönüşümü efekt

Küçük bir işlev olan `XForm`, özgün, açıklamalı ağaç öğesinden yeni bir dönüştürülmüş ağaç oluşturur.

İşlevin sahte kodu oldukça basittir:

> İşlevi bir XElement bağımsız değişken olarak alır ve bir XElement döndürür.
>
> Bir öğenin XElement ek açıklaması varsa, yeni bir XElement döndürün:
>
> - Yeni XElement adı ek açıklama öğesinin adıdır.
> - Tüm öznitelikler ek açıklamayla yeni düğüme kopyalanır.
> - Özel bir node: ApplyTransforms 'un tanındığından ve kaynak öğenin alt düğümleri tekrarlandırıldığından, tüm alt düğümler ek açıklamayla kopyalanır. Kaynak alt düğüm bir XElement değilse, yeni ağaca kopyalanır. Kaynak alt öğesi bir XElement ise, bu işlev yinelemeli olarak çağırarak dönüştürülür.
>
> Bir öğeye açıklama eklendiğinde:
>
> - Yeni bir XElement döndürün
>   - Yeni XElement adı, kaynak öğenin adıdır.
>   - Tüm öznitelikler, kaynak öğeden hedefin öğesine kopyalanır.
>   - Tüm alt düğümleri kaynak öğeden kopyalanır.
>   - Kaynak alt düğüm bir XElement değilse, yeni ağaca kopyalanır. Kaynak alt öğesi bir XElement ise, bu işlev yinelemeli olarak çağırarak dönüştürülür.

Aşağıdaki kod bu işlevin uygulamasıdır:

```vb
' Build a transformed XML tree per the annotations.
Function XForm(ByVal source As XElement) As XElement
    If source.Annotation(Of XElement)() IsNot Nothing Then
        Dim anno As XElement = source.Annotation(Of XElement)()
        Return _
            <<%= anno.Name.ToString() %>>
                <%= anno.Attributes() %>
                <%= anno.Nodes().Select(Function(n As XNode) _
                    GetSubNodes(n, source)) %>
            </>
    Else
        Return _
            <<%= source.Name %>>
                <%= source.Attributes() %>
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
            </>
    End If
End Function

Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
    Dim annoEl As XElement = TryCast(n, XElement)
    If annoEl IsNot Nothing Then
        If annoEl.Name = at Then
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
        End If
    End If
    Return n
End Function

Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
    Dim e2 As XElement = TryCast(n2, XElement)
    If e2 Is Nothing Then
        Return n2
    Else
        Return XForm(e2)
    End If
End Function
```

## <a name="complete-example"></a>Örnek Tamam

Aşağıdaki kod `XForm` işlevini içeren tam bir örnektir. Bu tür bir dönüştürme için tipik kullanımları içerir:

```vb
Imports System
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports System.Xml
Imports System.Xml.Linq

Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    ' Build a transformed XML tree per the annotations.
    Function XForm(ByVal source As XElement) As XElement
        If source.Annotation(Of XElement)() IsNot Nothing Then
            Dim anno As XElement = source.Annotation(Of XElement)()
            Return _
                <<%= anno.Name.ToString() %>>
                    <%= anno.Attributes() %>
                    <%= anno.Nodes().Select(Function(n As XNode) _
                        GetSubNodes(n, source)) %>
                </>
        Else
            Return _
                <<%= source.Name %>>
                    <%= source.Attributes() %>
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
                </>
        End If
    End Function

    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
        Dim annoEl As XElement = TryCast(n, XElement)
        If annoEl IsNot Nothing Then
            If annoEl.Name = at Then
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
            End If
        End If
        Return n
    End Function

    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
        Dim e2 As XElement = TryCast(n2, XElement)
        If e2 Is Nothing Then
            Return n2
        Else
            Return XForm(e2)
        End If
    End Function

    Sub Main()
        Dim root As XElement = _
<Root Att1='123'>
    <!--A comment-->
    <Child>1</Child>
    <Child>2</Child>
    <Other>
        <GC>3</GC>
        <GC>4</GC>
    </Other>
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
    <AnUnchangedElement>42</AnUnchangedElement>
</Root>

        ' Each of the following serves the same semantic purpose as
        ' XSLT templates and sequence constructors.

        ' Replace Child with NewChild.
        For Each el In root.<Child>
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)
        Next

        ' Replace first GC with GrandChild, add an attribute.
        For Each el In root...<GC>.Take(1)
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)
        Next

        ' Replace Other with NewOther, add new child elements around original content.
        For Each el In root.<Other>
            el.AddAnnotation( _
                <NewOther>
                    <MyNewChild>1</MyNewChild>
                    <<%= at %>></>
                    <ChildThatComesAfter/>
                </NewOther>)
        Next

        ' Change name of element that has mixed content.
        root...<SomeMixedContent>(0).AddAnnotation( _
                <MixedContent><<%= at %>></></MixedContent>)

        ' Replace <b> with <Bold>.
        For Each el In root...<b>
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)
        Next

        ' Replace <i> with <Italic>.
        For Each el In root...<i>
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)
        Next

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(root)
        Console.WriteLine(vbNewLine)
        Dim newRoot As XElement = XForm(root)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newRoot)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```console
Before Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <Child>1</Child>
  <Child>2</Child>
  <Other>
    <GC>3</GC>
    <GC>4</GC>
  </Other>
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>

After Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <NewChild>1</NewChild>
  <NewChild>2</NewChild>
  <NewOther>
    <MyNewChild>1</MyNewChild>
    <GrandChild ANewAttribute="999">3</GrandChild>
    <GC>4</GC>
    <ChildThatComesAfter />
  </NewOther>
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş LINQ to XML Programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

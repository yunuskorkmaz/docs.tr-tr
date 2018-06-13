---
title: 'Nasıl yapılır: LINQ-XML ağaçlarında XSLT stil (Visual Basic) dönüştürmek için ek açıklamalarını kullanma'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: c19d290e5b7acdf2702e24383a176ed06c9c7a1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650263"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a>Nasıl yapılır: LINQ-XML ağaçlarında XSLT stil (Visual Basic) dönüştürmek için ek açıklamalarını kullanma
Ek açıklamalar, bir XML ağacının dönüşümler kolaylaştırmak için kullanılabilir.  
  
 Bazı XML belgelerdir "Belge karışık içerikle merkezli." Bu tür belgelerle düğümleri bir öğenin alt şeklini mutlaka bilemeyebilirsiniz. Örneğin, metin içeren bir düğümü şu şekilde görünebilir:  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Verilen metni için herhangi bir düğümün, olabilir herhangi bir sayıda alt `<b>` ve `<i>` öğeleri. Bu yaklaşımın bir dizi diğer durum genişletir: gibi alt öğeleri, normal paragraflar, madde işaretli paragrafları ve bit eşlemler gibi çeşitli içerebilir sayfaları. Bir tablodaki hücre, metin içeren listeleri veya bit eşlemler bırakın. Belirli bir öğenin hangi alt öğesi bilmiyorsanız merkezli XML olan belge birincil özelliklerini biri.  
  
 Ardından ek açıklamaları kullanan bu yaklaşım burada mutlaka fazla dönüştürmek istediğiniz öğelerin alt tanımadığınız ağacındaki öğeler dönüştürmek istiyorsanız, etkili bir yaklaşımdır.  
  
 Yaklaşım özetidir:  
  
-   İlk olarak, bir değiştirme öğesi ağaç öğeleriyle açıklama.  
  
-   İkinci olarak, burada her öğe, ek açıklama Değiştir yeni ağacı oluşturma tüm ağaç yinelemek. Bu örnekte Yeni ağaç oluşturulmasını ve yineleme adlı bir işlev uygulayan `XForm`.  
  
 Ayrıntılı olarak yaklaşım oluşur:  
  
-   Bir şekle diğerine dönüştürmek istediğiniz öğeleri kümesini döndüren XML sorgular için bir veya daha fazla LINQ yürütün. Sorgudaki her öğe için yeni bir ekleme <xref:System.Xml.Linq.XElement> nesnesi olarak ek açıklama öğesi. Bu yeni öğe yeni, dönüştürülmüş ağacında ek açıklama öğesi yerini alır. Bu örnekte gösterildiği gibi yazmak için basit kodunu alırlar.  
  
-   Ek açıklamanın yeni alt düğümler içerebilir olarak eklenen yeni öğe; bir alt ağacı istenen herhangi bir şekilde oluşturabilir.  
  
-   Özel bir kural yok: farklı bir ad, bu amaçla oluşan bir ad alanı yeni öğesinin alt düğümü olup olmadığını (Bu örnekte ad alanıdır `http://www.microsoft.com/LinqToXmlTransform/2007`), sonra da bu alt öğesi yeni ağacına kopyalanmaz. Bunun yerine, ad alanı yukarıda sözü edilen özel ad alanı ve öğesinin yerel adı ise `ApplyTransforms`, kaynak ağacındaki öğesinin alt düğümleri yinelendiğinde ve yeni ağacıyla (açıklamalı alt öğeleri olan özel durum kopyalanır kendilerine bu kurallara göre dönüştürülen).  
  
-   Bu, biraz XSL Dönüşümleri belirtimini için benzerdir. Bir dizi düğümü seçer sorgu, bir şablon için XPath ifadesi benzerdir. Yeni oluşturmak için kodu <xref:System.Xml.Linq.XElement> açıklamanın XSL, dizisi oluşturucuda benzer olarak kaydedilir ve `ApplyTransforms` öğesidir işlev benzer `xsl:apply-templates` XSL öğesinde.  
  
-   Bu - yazarken yaklaşımı bir avantajı formüle sorguları, sorgu değiştirilmemiş kaynak ağaçta her zaman yazma. Ağaç değişiklikler yazmakta olduğunuz sorguları nasıl etkilediği hakkında endişe duymanız gerekmez.  
  
## <a name="transforming-a-tree"></a>Bir ağaç dönüştürme  
 Bu ilk örnek tüm yeniden adlandırır `Paragraph` düğümlerine `para`.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a>Daha karmaşık bir dönüştürme  
 Aşağıdaki örnek ağaç sorgular ve ortalama ve toplamını hesaplar `Data` öğeleri ve bunları ağaca olarak yeni öğeler ekler.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
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
  
## <a name="effecting-the-transform"></a>Dönüştürme etkili  
 Küçük bir işlevi `XForm`, yeni bir dönüştürülmüş ağacı açıklamalı, özgün ağacından oluşturur.  
  
-   İşlev için sahte kodu oldukça basittir:  
  
```  
The function takes an XElement as an argument and returns an XElement.   
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 Bu işlev uygulaması aşağıdadır:  
  
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
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kodu içeren tam bir örnek: `XForm` işlevi. Bu tür dönüştürme tipik kullanım alanlarından bazılarını içerir:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş LINQ-XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

---
title: 'Nasıl yapılır: XSLT stilinde LINQ to XML ağaçlarını dönüştürmek için ek açıklamaları kullanma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: aa0561ecc26139d191107521a8bb5fc2889332cd
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835069"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a><span data-ttu-id="f008b-102">Nasıl yapılır: XSLT stilinde LINQ to XML ağaçlarını dönüştürmek için ek açıklamaları kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f008b-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>
<span data-ttu-id="f008b-103">Ek açıklamalar, bir XML ağacının dönüştürmelerini kolaylaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f008b-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="f008b-104">Bazı XML belgeleri "karışık içerikli belge merkezli" dir.</span><span class="sxs-lookup"><span data-stu-id="f008b-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="f008b-105">Bu tür belgeler sayesinde bir öğenin alt düğümlerinin şeklini bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f008b-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="f008b-106">Örneğin, metin içeren bir düğüm şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="f008b-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="f008b-107">Herhangi bir metin düğümü için herhangi bir sayıda alt `<b>` ve `<i>` öğe olabilir.</span><span class="sxs-lookup"><span data-stu-id="f008b-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="f008b-108">Bu yaklaşım birkaç farklı durum sağlar: gibi, normal paragraflar, madde işaretli paragraflar ve bit eşlemler gibi çeşitli alt öğeler içerebilen sayfalar.</span><span class="sxs-lookup"><span data-stu-id="f008b-108">This approach extends to a number of other situations: such as, pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="f008b-109">Bir tablodaki hücreler metin, açılan liste veya bit eşlemler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f008b-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="f008b-110">Belge merkezli XML 'in birincil özelliklerinden biri, belirli bir öğenin hangi alt öğesi olacağını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f008b-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="f008b-111">Dönüştürmek istediğiniz öğelerin alt öğeleri hakkında daha fazla bilgi sahibi olmadığınız bir ağaçtaki öğeleri dönüştürmek istiyorsanız, ek açıklamaları kullanan bu yaklaşım etkili bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="f008b-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="f008b-112">Yaklaşımın Özeti:</span><span class="sxs-lookup"><span data-stu-id="f008b-112">The summary of the approach is:</span></span>  
  
- <span data-ttu-id="f008b-113">İlk olarak, ağaç içindeki öğeleri bir değiştirme öğesiyle birlikte not edin.</span><span class="sxs-lookup"><span data-stu-id="f008b-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
- <span data-ttu-id="f008b-114">İkinci olarak, tüm ağaç üzerinde yineleme yapın, her öğeyi ek açıklamasına göre değiştirdiğiniz yeni bir ağaç oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f008b-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="f008b-115">Bu örnek, `XForm` adlı bir işlevde yeni ağacın yinelemesini ve oluşturulmasını uygular.</span><span class="sxs-lookup"><span data-stu-id="f008b-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="f008b-116">Ayrıntılı olarak yaklaşım aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="f008b-116">In detail, the approach consists of:</span></span>  
  
- <span data-ttu-id="f008b-117">Bir şekilden diğerine dönüştürmek istediğiniz öğe kümesini döndüren bir veya daha fazla LINQ to XML sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="f008b-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="f008b-118">Sorgudaki her öğe için, öğeye ek açıklama olarak yeni bir <xref:System.Xml.Linq.XElement> nesnesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f008b-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="f008b-119">Bu yeni öğe, yeni, dönüştürülmüş ağaçtaki açıklamalı öğenin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="f008b-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="f008b-120">Bu, örnekte gösterildiği gibi yazılacak basit koddur.</span><span class="sxs-lookup"><span data-stu-id="f008b-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
- <span data-ttu-id="f008b-121">Ek açıklama olarak eklenen yeni öğe, yeni alt düğümler içerebilir; istediğiniz herhangi bir şekle sahip bir alt ağaç oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="f008b-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
- <span data-ttu-id="f008b-122">Özel bir kural var: yeni öğenin bir alt düğümü, bu amaçla oluşturulan bir ad alanı, farklı bir ad alanında ise (Bu örnekte, ad alanı `http://www.microsoft.com/LinqToXmlTransform/2007`), bu alt öğe yeni ağaca kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="f008b-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="f008b-123">Bunun yerine, ad alanı yukarıda belirtilen özel ad alanıdır ve öğenin yerel adı `ApplyTransforms` ise, Kaynak ağacındaki öğenin alt düğümleri yinelenir ve yeni ağaca kopyalanır (ek açıklamalı alt öğelerin olduğu özel durum ile). kendileri bu kurallara göre dönüştürülür).</span><span class="sxs-lookup"><span data-stu-id="f008b-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
- <span data-ttu-id="f008b-124">Bu, XSL 'teki dönüşümler belirtimine benzer.</span><span class="sxs-lookup"><span data-stu-id="f008b-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="f008b-125">Düğüm kümesi seçen sorgu, bir şablon için XPath ifadesine benzer.</span><span class="sxs-lookup"><span data-stu-id="f008b-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="f008b-126">Ek açıklama olarak kaydedilen yeni @no__t oluşturma kodu, XSL 'deki dizi oluşturucusuna benzerdir ve `ApplyTransforms` öğesi, XSL içindeki `xsl:apply-templates` öğesine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f008b-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
- <span data-ttu-id="f008b-127">Bu yaklaşımı almanın avantajlarından biri olan sorgular, her zaman değiştirilmemiş kaynak ağacına sorgu yazırsınız.</span><span class="sxs-lookup"><span data-stu-id="f008b-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="f008b-128">Ağaçta yapılan değişikliklerin yazmakta olduğunuz sorguları nasıl etkilediği konusunda endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f008b-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="f008b-129">Ağacı dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f008b-129">Transforming a Tree</span></span>  
 <span data-ttu-id="f008b-130">Bu ilk örnek, tüm `Paragraph` düğümlerini `para` olarak yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="f008b-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
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
  
 <span data-ttu-id="f008b-131">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f008b-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="f008b-132">Daha karmaşık bir dönüşüm</span><span class="sxs-lookup"><span data-stu-id="f008b-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="f008b-133">Aşağıdaki örnek, ağacı sorgular ve `Data` öğelerinin ortalamasını ve toplamını hesaplar ve bunları ağaca yeni öğeler olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="f008b-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
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
  
 <span data-ttu-id="f008b-134">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f008b-134">This example produces the following output:</span></span>  
  
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
  
## <a name="effecting-the-transform"></a><span data-ttu-id="f008b-135">Dönüşümü efekt</span><span class="sxs-lookup"><span data-stu-id="f008b-135">Effecting the Transform</span></span>  
 <span data-ttu-id="f008b-136">Küçük bir işlev olan `XForm`, özgün, açıklamalı ağaç öğesinden yeni bir dönüştürülmüş ağaç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f008b-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
<span data-ttu-id="f008b-137">İşlevin sahte kodu oldukça basittir:</span><span class="sxs-lookup"><span data-stu-id="f008b-137">The pseudo code for the function is quite simple:</span></span>  
  
> <span data-ttu-id="f008b-138">İşlevi bir XElement bağımsız değişken olarak alır ve bir XElement döndürür.</span><span class="sxs-lookup"><span data-stu-id="f008b-138">The function takes an XElement as an argument and returns an XElement.</span></span>
>   
> <span data-ttu-id="f008b-139">Bir öğenin XElement ek açıklaması varsa, yeni bir XElement döndürün:</span><span class="sxs-lookup"><span data-stu-id="f008b-139">If an element has an XElement annotation, then return a new XElement:</span></span>  
>    - <span data-ttu-id="f008b-140">Yeni XElement adı ek açıklama öğesinin adıdır.</span><span class="sxs-lookup"><span data-stu-id="f008b-140">The name of the new XElement is the annotation element's name.</span></span>  
>    - <span data-ttu-id="f008b-141">Tüm öznitelikler ek açıklamayla yeni düğüme kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f008b-141">All attributes are copied from the annotation to the new node.</span></span>  
>    - <span data-ttu-id="f008b-142">Özel bir node: ApplyTransforms 'un tanındığından ve kaynak öğenin alt düğümleri tekrarlandırıldığından, tüm alt düğümler ek açıklamayla kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f008b-142">All child nodes are copied from the annotation, with the exception that the special node xf:ApplyTransforms is recognized, and the source element's child nodes are iterated.</span></span> <span data-ttu-id="f008b-143">Kaynak alt düğüm bir XElement değilse, yeni ağaca kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f008b-143">If the source child node is not an XElement, it is copied to the new tree.</span></span> <span data-ttu-id="f008b-144">Kaynak alt öğesi bir XElement ise, bu işlev yinelemeli olarak çağırarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f008b-144">If the source child is an XElement, then it is transformed by calling this function recursively.</span></span>
>  
> <span data-ttu-id="f008b-145">Bir öğeye açıklama eklendiğinde:</span><span class="sxs-lookup"><span data-stu-id="f008b-145">If an element is not annotated:</span></span>  
>    - <span data-ttu-id="f008b-146">Yeni bir XElement döndürün</span><span class="sxs-lookup"><span data-stu-id="f008b-146">Return a new XElement</span></span>  
>        - <span data-ttu-id="f008b-147">Yeni XElement adı, kaynak öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="f008b-147">The name of the new XElement is the source element's name.</span></span>  
>        - <span data-ttu-id="f008b-148">Tüm öznitelikler, kaynak öğeden hedefin öğesine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f008b-148">All attributes are copied from the source element to the destination's element.</span></span>  
>        - <span data-ttu-id="f008b-149">Tüm alt düğümleri kaynak öğeden kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f008b-149">All child nodes are copied from the source element.</span></span>  
>        - <span data-ttu-id="f008b-150">Kaynak alt düğüm bir XElement değilse, yeni ağaca kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f008b-150">If the source child node is not an XElement, it is copied to the new tree.</span></span> <span data-ttu-id="f008b-151">Kaynak alt öğesi bir XElement ise, bu işlev yinelemeli olarak çağırarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f008b-151">If the source child is an XElement, then it is transformed by calling this function recursively.</span></span>  

<span data-ttu-id="f008b-152">Bu işlevin uygulanması aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f008b-152">The Following is the implementation of this function:</span></span>  
  
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
  
## <a name="complete-example"></a><span data-ttu-id="f008b-153">Örnek Tamam</span><span class="sxs-lookup"><span data-stu-id="f008b-153">Complete Example</span></span>  
 <span data-ttu-id="f008b-154">Aşağıdaki kod `XForm` işlevini içeren tam bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="f008b-154">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="f008b-155">Bu tür bir dönüştürme için tipik kullanımları içerir:</span><span class="sxs-lookup"><span data-stu-id="f008b-155">It includes a few of the typical uses of this type of transform:</span></span>  
  
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
  
 <span data-ttu-id="f008b-156">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f008b-156">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f008b-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f008b-157">See also</span></span>

- [<span data-ttu-id="f008b-158">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f008b-158">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

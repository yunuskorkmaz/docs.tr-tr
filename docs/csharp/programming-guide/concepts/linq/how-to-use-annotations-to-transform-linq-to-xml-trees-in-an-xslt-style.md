---
title: 'Nasıl yapılır: LINQ-XML ağaçları bir XSLT stilde (C#) dönüştürmek için ek açıklamalarını kullanma'
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 551be4fe39bcfc9fd5492366014322d78416ba58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328844"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a><span data-ttu-id="0cdd6-102">Nasıl yapılır: LINQ-XML ağaçları bir XSLT stilde (C#) dönüştürmek için ek açıklamalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="0cdd6-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (C#)</span></span>
<span data-ttu-id="0cdd6-103">Ek açıklamalar, bir XML ağacının dönüşümler kolaylaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="0cdd6-104">Bazı XML belgelerdir "Belge karışık içerikle merkezli."</span><span class="sxs-lookup"><span data-stu-id="0cdd6-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="0cdd6-105">Bu tür belgelerle düğümleri bir öğenin alt şeklini mutlaka bilemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="0cdd6-106">Örneğin, metin içeren bir düğümü şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="0cdd6-107">Verilen metni için herhangi bir düğümün, olabilir herhangi bir sayıda alt `<b>` ve `<i>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="0cdd6-108">Bu yaklaşım, alt öğeleri, normal paragraflar, madde işaretli paragrafları ve bit eşlemler gibi çeşitli içerebilir sayfaları gibi diğer durumlarda, bir dizi genişletir.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-108">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="0cdd6-109">Bir tablodaki hücre, metin içeren listeleri veya bit eşlemler bırakın.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="0cdd6-110">Belirli bir öğenin hangi alt öğesi bilmiyorsanız merkezli XML olan belge birincil özelliklerini biri.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="0cdd6-111">Ardından ek açıklamaları kullanan bu yaklaşım burada mutlaka fazla dönüştürmek istediğiniz öğelerin alt tanımadığınız ağacındaki öğeler dönüştürmek istiyorsanız, etkili bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="0cdd6-112">Yaklaşım özetidir:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-112">The summary of the approach is:</span></span>  
  
-   <span data-ttu-id="0cdd6-113">İlk olarak, bir değiştirme öğesi ağaç öğeleriyle açıklama.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
-   <span data-ttu-id="0cdd6-114">İkinci olarak, burada her öğe, ek açıklama Değiştir yeni ağacı oluşturma tüm ağaç yinelemek.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="0cdd6-115">Bu örnekte Yeni ağaç oluşturulmasını ve yineleme adlı bir işlev uygulayan `XForm`.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="0cdd6-116">Ayrıntılı olarak yaklaşım oluşur:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-116">In detail, the approach consists of:</span></span>  
  
-   <span data-ttu-id="0cdd6-117">Bir şekle diğerine dönüştürmek istediğiniz öğeleri kümesini döndüren XML sorgular için bir veya daha fazla LINQ yürütün.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="0cdd6-118">Sorgudaki her öğe için yeni bir ekleme <xref:System.Xml.Linq.XElement> nesnesi olarak ek açıklama öğesi.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="0cdd6-119">Bu yeni öğe yeni, dönüştürülmüş ağacında ek açıklama öğesi yerini alır.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="0cdd6-120">Bu örnekte gösterildiği gibi yazmak için basit kodunu alırlar.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
-   <span data-ttu-id="0cdd6-121">Ek açıklamanın yeni alt düğümler içerebilir olarak eklenen yeni öğe; bir alt ağacı istenen herhangi bir şekilde oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
-   <span data-ttu-id="0cdd6-122">Özel bir kural yok: farklı bir ad, bu amaçla oluşan bir ad alanı yeni öğesinin alt düğümü olup olmadığını (Bu örnekte ad alanıdır `http://www.microsoft.com/LinqToXmlTransform/2007`), sonra da bu alt öğesi yeni ağacına kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="0cdd6-123">Bunun yerine, ad alanı yukarıda sözü edilen özel ad alanı ve öğesinin yerel adı ise `ApplyTransforms`, kaynak ağacındaki öğesinin alt düğümleri yinelendiğinde ve yeni ağacıyla (açıklamalı alt öğeleri olan özel durum kopyalanır kendilerine bu kurallara göre dönüştürülen).</span><span class="sxs-lookup"><span data-stu-id="0cdd6-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
-   <span data-ttu-id="0cdd6-124">Bu, biraz XSL Dönüşümleri belirtimini için benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="0cdd6-125">Bir dizi düğümü seçer sorgu, bir şablon için XPath ifadesi benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="0cdd6-126">Yeni oluşturmak için kodu <xref:System.Xml.Linq.XElement> açıklamanın XSL, dizisi oluşturucuda benzer olarak kaydedilir ve `ApplyTransforms` öğesidir işlev benzer `xsl:apply-templates` XSL öğesinde.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
-   <span data-ttu-id="0cdd6-127">Bu - yazarken yaklaşımı bir avantajı formüle sorguları, sorgu değiştirilmemiş kaynak ağaçta her zaman yazma.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="0cdd6-128">Ağaç değişiklikler yazmakta olduğunuz sorguları nasıl etkilediği hakkında endişe duymanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="0cdd6-129">Bir ağaç dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0cdd6-129">Transforming a Tree</span></span>  
 <span data-ttu-id="0cdd6-130">Bu ilk örnek tüm yeniden adlandırır `Paragraph` düğümlerine `para`.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement root = XElement.Parse(@"  
<Root>  
    <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
    <Paragraph>More text.</Paragraph>  
</Root>");  
  
// replace Paragraph with para  
foreach (var el in root.Descendants("Paragraph"))  
    el.AddAnnotation(  
        new XElement("para",  
            // same idea as xsl:apply-templates  
            new XElement(xf + "ApplyTransforms")  
        )  
    );  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newRoot = XForm(root);  
  
Console.WriteLine(newRoot);  
```  
  
 <span data-ttu-id="0cdd6-131">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="0cdd6-132">Daha karmaşık bir dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0cdd6-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="0cdd6-133">Aşağıdaki örnek ağaç sorgular ve ortalama ve toplamını hesaplar `Data` öğeleri ve bunları ağaca olarak yeni öğeler ekler.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement data = new XElement("Root",  
    new XElement("Data", 20),  
    new XElement("Data", 10),  
    new XElement("Data", 3)  
);  
  
// while adding annotations, you can query the source tree all you want,  
// as the tree is not mutated while annotating.  
data.AddAnnotation(  
    new XElement("Root",  
        new XElement(xf + "ApplyTransforms"),  
        new XElement("Average",  
            String.Format("{0:F4}",  
                data  
                .Elements("Data")  
                .Select(z => (Decimal)z)  
                .Average()  
            )  
        ),  
        new XElement("Sum",  
            data  
            .Elements("Data")  
            .Select(z => (int)z)  
            .Sum()  
        )  
    )  
);  
  
Console.WriteLine("Before Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(data);  
Console.WriteLine();  
Console.WriteLine();  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newData = XForm(data);  
  
Console.WriteLine("After Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="0cdd6-134">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-134">This example produces the following output:</span></span>  
  
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
  
## <a name="effecting-the-transform"></a><span data-ttu-id="0cdd6-135">Dönüştürme etkili</span><span class="sxs-lookup"><span data-stu-id="0cdd6-135">Effecting the Transform</span></span>  
 <span data-ttu-id="0cdd6-136">Küçük bir işlevi `XForm`, yeni bir dönüştürülmüş ağacı açıklamalı, özgün ağacından oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
-   <span data-ttu-id="0cdd6-137">İşlev için sahte kodu oldukça basittir:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-137">The pseudo code for the function is quite simple:</span></span>  
  
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
  
 <span data-ttu-id="0cdd6-138">Bu işlev uygulaması aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-138">Following is the implementation of this function:</span></span>  
  
```csharp  
// Build a transformed XML tree per the annotations  
static XElement XForm(XElement source)  
{  
    XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    XName at = xf + "ApplyTransforms";  
  
    if (source.Annotation<XElement>() != null)  
    {  
        XElement anno = source.Annotation<XElement>();  
        return new XElement(anno.Name,  
            anno.Attributes(),  
            anno  
            .Nodes()  
            .Select(  
                (XNode n) =>  
                {  
                    XElement annoEl = n as XElement;  
                    if (annoEl != null)  
                    {  
                        if (annoEl.Name == at)  
                            return (object)(  
                                source.Nodes()  
                                .Select(  
                                    (XNode n2) =>  
                                    {  
                                        XElement e2 = n2 as XElement;  
                                        if (e2 == null)  
                                            return n2;  
                                        else  
                                            return XForm(e2);  
                                    }  
                                )  
                            );  
                        else  
                            return n;  
                    }  
                    else  
                        return n;  
                }  
            )  
        );  
    }  
    else  
    {  
        return new XElement(source.Name,  
            source.Attributes(),  
            source  
                .Nodes()  
                .Select(n =>  
                {  
                    XElement el = n as XElement;  
                    if (el == null)  
                        return n;  
                    else  
                        return XForm(el);  
                }  
                )  
        );  
    }  
}   
```  
  
## <a name="complete-example"></a><span data-ttu-id="0cdd6-139">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="0cdd6-139">Complete Example</span></span>  
 <span data-ttu-id="0cdd6-140">Aşağıdaki kodu içeren tam bir örnek: `XForm` işlevi.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="0cdd6-141">Bu tür dönüştürme tipik kullanım alanlarından bazılarını içerir:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Xml;  
using System.Xml.Linq;  
  
class Program  
{  
    static XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    static XName at = xf + "ApplyTransforms";  
  
    // Build a transformed XML tree per the annotations  
    static XElement XForm(XElement source)  
    {  
        if (source.Annotation<XElement>() != null)  
        {  
            XElement anno = source.Annotation<XElement>();  
            return new XElement(anno.Name,  
                anno.Attributes(),  
                anno  
                .Nodes()  
                .Select(  
                    (XNode n) =>  
                    {  
                        XElement annoEl = n as XElement;  
                        if (annoEl != null)  
                        {  
                            if (annoEl.Name == at)  
                                return (object)(  
                                    source.Nodes()  
                                    .Select(  
                                        (XNode n2) =>  
                                        {  
                                            XElement e2 = n2 as XElement;  
                                            if (e2 == null)  
                                                return n2;  
                                            else  
                                                return XForm(e2);  
                                        }  
                                    )  
                                );  
                            else  
                                return n;  
                        }  
                        else  
                            return n;  
                    }  
                )  
            );  
        }  
        else  
        {  
            return new XElement(source.Name,  
                source.Attributes(),  
                source  
                    .Nodes()  
                    .Select(n =>  
                    {  
                        XElement el = n as XElement;  
                        if (el == null)  
                            return n;  
                        else  
                            return XForm(el);  
                    }  
                    )  
            );  
        }  
    }  
  
    static void Main(string[] args)  
    {  
        XElement root = new XElement("Root",  
            new XComment("A comment"),  
            new XAttribute("Att1", 123),  
            new XElement("Child", 1),  
            new XElement("Child", 2),  
            new XElement("Other",  
                new XElement("GC", 3),  
                new XElement("GC", 4)  
            ),  
            XElement.Parse(  
              "<SomeMixedContent>This is <i>an</i> element that " +  
              "<b>has</b> some mixed content</SomeMixedContent>"),  
            new XElement("AnUnchangedElement", 42)  
        );  
  
        // each of the following serves the same semantic purpose as  
        // XSLT templates and sequence constructors  
  
        // replace Child with NewChild  
        foreach (var el in root.Elements("Child"))  
            el.AddAnnotation(new XElement("NewChild", (string)el));  
  
        // replace first GC with GrandChild, add an attribute  
        foreach (var el in root.Descendants("GC").Take(1))  
            el.AddAnnotation(  
                new XElement("GrandChild",  
                    new XAttribute("ANewAttribute", 999),  
                    (string)el  
                )  
            );  
  
        // replace Other with NewOther, add new child elements around original content  
        foreach (var el in root.Elements("Other"))  
            el.AddAnnotation(  
                new XElement("NewOther",  
                    new XElement("MyNewChild", 1),  
                    // same idea as xsl:apply-templates  
                    new XElement(xf + "ApplyTransforms"),  
                    new XElement("ChildThatComesAfter")  
                )  
            );  
  
        // change name of element that has mixed content  
        root.Descendants("SomeMixedContent").First().AddAnnotation(  
            new XElement("MixedContent",  
                new XElement(xf + "ApplyTransforms")  
            )  
        );  
  
        // replace <b> with <Bold>  
        foreach (var el in root.Descendants("b"))  
            el.AddAnnotation(  
                new XElement("Bold",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        // replace <i> with <Italic>  
        foreach (var el in root.Descendants("i"))  
            el.AddAnnotation(  
                new XElement("Italic",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        Console.WriteLine("Before Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(root);  
        Console.WriteLine();  
        Console.WriteLine();  
        XElement newRoot = XForm(root);  
  
        Console.WriteLine("After Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(newRoot);  
    }  
}  
```  
  
 <span data-ttu-id="0cdd6-142">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="0cdd6-142">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cdd6-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0cdd6-143">See Also</span></span>  
 [<span data-ttu-id="0cdd6-144">Gelişmiş LINQ-XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="0cdd6-144">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

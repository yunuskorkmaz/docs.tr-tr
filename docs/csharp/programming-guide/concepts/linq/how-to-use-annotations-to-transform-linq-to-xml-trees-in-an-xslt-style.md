---
title: 'Nasıl yapılır: LINQ-XML ağaçları bir XSLT stilde (C#) dönüştürmek için ek açıklamalarını kullanma'
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 551be4fe39bcfc9fd5492366014322d78416ba58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a>Nasıl yapılır: LINQ-XML ağaçları bir XSLT stilde (C#) dönüştürmek için ek açıklamalarını kullanma
Ek açıklamalar, bir XML ağacının dönüşümler kolaylaştırmak için kullanılabilir.  
  
 Bazı XML belgelerdir "Belge karışık içerikle merkezli." Bu tür belgelerle düğümleri bir öğenin alt şeklini mutlaka bilemeyebilirsiniz. Örneğin, metin içeren bir düğümü şu şekilde görünebilir:  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Verilen metni için herhangi bir düğümün, olabilir herhangi bir sayıda alt `<b>` ve `<i>` öğeleri. Bu yaklaşım, alt öğeleri, normal paragraflar, madde işaretli paragrafları ve bit eşlemler gibi çeşitli içerebilir sayfaları gibi diğer durumlarda, bir dizi genişletir. Bir tablodaki hücre, metin içeren listeleri veya bit eşlemler bırakın. Belirli bir öğenin hangi alt öğesi bilmiyorsanız merkezli XML olan belge birincil özelliklerini biri.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a>Daha karmaşık bir dönüştürme  
 Aşağıdaki örnek ağaç sorgular ve ortalama ve toplamını hesaplar `Data` öğeleri ve bunları ağaca olarak yeni öğeler ekler.  
  
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
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kodu içeren tam bir örnek: `XForm` işlevi. Bu tür dönüştürme tipik kullanım alanlarından bazılarını içerir:  
  
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
 [Gelişmiş LINQ-XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

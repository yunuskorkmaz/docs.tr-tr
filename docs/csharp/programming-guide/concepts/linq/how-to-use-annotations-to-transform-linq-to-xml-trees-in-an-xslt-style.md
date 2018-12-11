---
title: 'Nasıl Yapılır: LINQ to XML ağaçlarını XSLT stilindeki dönüştürmek için ek açıklamalarını kullanma (C#)'
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: c93ba3209b80cf2467c0f3b49dc25e729c6a14c6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144539"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a>Nasıl Yapılır: LINQ to XML ağaçlarını XSLT stilindeki dönüştürmek için ek açıklamalarını kullanma (C#)
Ek açıklamalar, XML ağacının dönüşümler kolaylaştırmak için kullanılabilir.  
  
 Bazı XML belgelerdir "belge ile karışık içerik merkezli." Bu belge, bir öğe düğümlerinin alt şeklin mutlaka bilmiyorum. Örneğin, metin içeren bir düğüm şöyle görünebilir:  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Herhangi bir belirli metin düğümü için olabilir herhangi bir sayıda alt `<b>` ve `<i>` öğeleri. Bu yaklaşım, bir dizi alt öğeleri, bit eşlemler normal paragraflar ve madde işaretli paragrafları gibi çeşitli içerebilir sayfaları gibi diğer durumlarda genişletir. Bir tablodaki hücre, metin içeren listeleri veya bit eşlemler bırakın. Belirli bir öğenin olacaktır hangi alt öğesi bilmiyorsanız merkezli XML olan belge birincil özelliklerini biri.  
  
 Burada mutlaka dönüştürmek istediğiniz öğeleri alt hakkında pek fazla bilmediğiniz bir ağaç öğesinde dönüştürmek istiyorsanız, daha sonra ek açıklamaları kullanan bu etkili bir yaklaşım yaklaşımdır.  
  
 Yaklaşım özetidir:  
  
-   İlk olarak, bir değiştirme öğesi ağaç öğeleriyle açıklama ekleyin.  
  
-   İkinci olarak, burada her öğe, ek açıklama ile değiştirin ve yeni bir ağaç oluşturma ağacının tümünü yineleyin. Bu örnek adlı bir işlevde yeni ağaç oluşturulmasını ve yineleme uygulayan `XForm`.  
  
 Ayrıntılı olarak yaklaşım oluşur:  
  
-   Bir veya daha fazla LINQ to bir şekilden diğerine dönüştürmek istediğiniz öğeleri kümesi döndüren XML sorgular yürütün. Sorgudaki her öğe için yeni bir ekleme <xref:System.Xml.Linq.XElement> öğeye bir eklenti olarak nesnesi. Bu yeni öğe yeni, dönüştürülen ağacında açıklamalı öğenin yerini alır. Basit kod yazmak için örnekte gösterildiği gibi budur.  
  
-   Ek açıklamanın yeni alt düğümleri içermesi gibi eklenen yeni öğe; Bu, bir alt ağacı istenen herhangi bir şekilde oluşturabilir.  
  
-   Özel bir kural yoktur: Yeni öğenin bir alt düğüm farklı bir ad alanında bu amaçla yapılmış bir ad alanı olup olmadığını (Bu örnekte ad alanı `http://www.microsoft.com/LinqToXmlTransform/2007`), o alt öğe yeni ağacına kopyalanır değil. Bunun yerine, ad alanı yukarıda belirtilen özel ad alanı ve öğe yerel adı ise `ApplyTransforms`, kaynak ağacının öğenin alt düğümleri yinelenir ve yeni ağaçta (açıklamalı alt öğeleri olan özel durum kopyalanır kendilerine bu kurallara göre dönüştürülür).  
  
-   XSL içindeki dönüşümler belirtimi soyguna budur. Bir dizi düğümü seçer sorgu, bir şablon için XPath ifadesi benzerdir. Yeni kod <xref:System.Xml.Linq.XElement> açıklamanın XSL, sıralı oluşturucuda benzer olarak kaydedilir ve `ApplyTransforms` öğedir işlev benzer `xsl:apply-templates` XSL öğesinde.  
  
-   -Yazarken bu yaklaşımı uygularsanız bir avantajı, sorgu değiştirilmemiş kaynak ağacında her zaman yazma sorguları düzenleyin. Ağaç yapılan değişiklikler, yazmakta olduğunuz sorguları nasıl etkilediğini hakkında endişe duymanız gerekmez.  
  
## <a name="transforming-a-tree"></a>Bir ağaç dönüştürme  
 Bu ilk örnekte tüm yeniden adlandırır `Paragraph` düğümlerine `para`.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a>Daha karmaşık bir dönüştürme  
 Aşağıdaki örnek ağaç sorgular ve ortalama ve toplamı hesaplar `Data` öğeleri ve bunları ağacına kadar yeni öğeler ekler.  
  
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
var avg = data.Elements("Data").Select(z => (Decimal)z).Average();
data.AddAnnotation(  
    new XElement("Root",  
        new XElement(xf + "ApplyTransforms"),  
        new XElement("Average", $"{avg:F4}"),
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
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
  
## <a name="effecting-the-transform"></a>Dönüştürme etkileyen  
 Küçük bir işlevi `XForm`, yeni dönüştürülmüş ağacı özgün, ek açıklamalı ağacından oluşturur.  
  
-   İşlev için sahte kod oldukça basittir:  
  
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
  
 Bu işlev uygulamasını aşağıda verilmiştir:  
  
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
 Aşağıdaki kodu içeren tam bir örnek olduğundan `XForm` işlevi. Bu tür bir dönüştürme tipik kullanımları birkaçını içerir:  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
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

- [Gelişmiş LINQ to XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

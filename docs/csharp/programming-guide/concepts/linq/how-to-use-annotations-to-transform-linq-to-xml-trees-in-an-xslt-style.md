---
title: XSLT stilinde (C#) LINQ to XML ağaçlarını dönüştürmek için ek açıklamalar kullanma
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 109e1a49530f34e7197f8c975de8c04245b11734
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347291"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a>XSLT stilinde (C#) LINQ to XML ağaçlarını dönüştürmek için ek açıklamalar kullanma
Ek açıklamalar, bir XML ağacının dönüştürmelerini kolaylaştırmak için kullanılabilir.  
  
 Bazı XML belgeleri "karışık içerikli belge merkezli" dir. Bu tür belgeler sayesinde bir öğenin alt düğümlerinin şeklini bilmeniz gerekmez. Örneğin, metin içeren bir düğüm şöyle görünebilir:  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Herhangi bir metin düğümü için herhangi bir sayıda alt `<b>` ve `<i>` öğesi olabilir. Bu yaklaşım, normal paragraflar, madde işaretli paragraflar ve bit eşlemler gibi çeşitli alt öğeler içerebilen sayfalar gibi bir dizi diğer durum için genişler. Bir tablodaki hücreler metin, açılan liste veya bit eşlemler içerebilir. Belge merkezli XML 'in birincil özelliklerinden biri, belirli bir öğenin hangi alt öğesi olacağını bilemezsiniz.  
  
 Dönüştürmek istediğiniz öğelerin alt öğeleri hakkında daha fazla bilgi sahibi olmadığınız bir ağaçtaki öğeleri dönüştürmek istiyorsanız, ek açıklamaları kullanan bu yaklaşım etkili bir yaklaşımdır.  
  
 Yaklaşımın Özeti:  
  
- İlk olarak, ağaç içindeki öğeleri bir değiştirme öğesiyle birlikte not edin.  
  
- İkinci olarak, tüm ağaç üzerinde yineleme yapın, her öğeyi ek açıklamasına göre değiştirdiğiniz yeni bir ağaç oluşturun. Bu örnek, `XForm`adlı bir işlevde yeni ağacın yinelemesini ve oluşturulmasını uygular.  
  
 Ayrıntılı olarak yaklaşım aşağıdakilerden oluşur:  
  
- Bir şekilden diğerine dönüştürmek istediğiniz öğe kümesini döndüren bir veya daha fazla LINQ to XML sorgu yürütün. Sorgudaki her öğe için, öğesine ek açıklama olarak yeni bir <xref:System.Xml.Linq.XElement> nesnesi ekleyin. Bu yeni öğe, yeni, dönüştürülmüş ağaçtaki açıklamalı öğenin yerini alır. Bu, örnekte gösterildiği gibi yazılacak basit koddur.  
  
- Ek açıklama olarak eklenen yeni öğe, yeni alt düğümler içerebilir; istediğiniz herhangi bir şekle sahip bir alt ağaç oluşturabilir.  
  
- Özel bir kural var: yeni öğenin bir alt düğümü, bu amaçla oluşturulan bir ad alanı, farklı bir ad alanında ise (Bu örnekte, ad alanı `http://www.microsoft.com/LinqToXmlTransform/2007`), bu alt öğe yeni ağaca kopyalanmaz. Bunun yerine, ad alanı yukarıda belirtilen özel ad alanıdır ve öğenin yerel adı `ApplyTransforms`, ardından Kaynak ağacındaki öğenin alt düğümleri yinelenir ve yeni ağaca kopyalanır (ek açıklama alt öğelerinin kendileri bu kurallara göre dönüştürülür).  
  
- Bu, XSL 'teki dönüşümler belirtimine benzer. Düğüm kümesi seçen sorgu, bir şablon için XPath ifadesine benzer. Ek açıklama olarak kaydedilen yeni <xref:System.Xml.Linq.XElement> oluşturma kodu, XSL 'deki dizi oluşturucusuna benzerdir ve `ApplyTransforms` öğesi, XSL içindeki `xsl:apply-templates` öğesine benzerdir.  
  
- Bu yaklaşımı almanın avantajlarından biri olan sorgular, her zaman değiştirilmemiş kaynak ağacına sorgu yazırsınız. Ağaçta yapılan değişikliklerin yazmakta olduğunuz sorguları nasıl etkilediği konusunda endişelenmeniz gerekmez.  
  
## <a name="transforming-a-tree"></a>Ağacı dönüştürme  
 Bu ilk örnek, tüm `Paragraph` düğümlerini `para`olarak yeniden adlandırır.  
  
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
  
## <a name="a-more-complicated-transform"></a>Daha karmaşık bir dönüşüm  
 Aşağıdaki örnek, ağacı sorgular ve `Data` öğelerinin ortalamasını ve toplamını hesaplar ve bunları ağaca yeni öğeler olarak ekler.  
  
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
  
```output  
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
 Küçük bir işlev, `XForm`, orijinal, açıklamalı ağaç ' dan yeni bir dönüştürülmüş ağaç oluşturur.  
  
- İşlevin sahte kodu oldukça basittir:  
  
```text  
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
  
 Bu işlevin uygulanması aşağıda verilmiştir:  
  
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
 Aşağıdaki kod, `XForm` işlevini içeren bir bütün örnektir. Bu tür bir dönüştürme için tipik kullanımları içerir:  
  
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
  
```output  
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
  
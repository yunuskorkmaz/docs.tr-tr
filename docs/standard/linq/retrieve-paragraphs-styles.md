---
title: Paragrafları ve stillerini alma-LINQ to XML
description: WordprocessingML belgesinden paragraf düğümlerini ve bunların stillerini almayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 43c6173441dda841236a4397e28d0bb2c7c8d003
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553882"
---
# <a name="retrieve-the-paragraphs-and-their-styles-linq-to-xml"></a><span data-ttu-id="5a05c-103">Paragrafları ve stillerini alma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5a05c-103">Retrieve the paragraphs and their styles (LINQ to XML)</span></span>

<span data-ttu-id="5a05c-104">Bu örnekte, bir WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazdık.</span><span class="sxs-lookup"><span data-stu-id="5a05c-104">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="5a05c-105">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="5a05c-105">It also identifies the style of each paragraph.</span></span>

<span data-ttu-id="5a05c-106">Bu sorgu, önceki örnekteki sorgu üzerinde yapılar, varsayılan stili stil listesinden alan [varsayılan paragraf stilini bulur](find-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="5a05c-106">This query builds on the query in the previous example, [Find the default paragraph style](find-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="5a05c-107">Bu bilgiler, sorgunun açıkça ayarlanmış bir stile sahip olmayan paragrafların stilini belirleyebilmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5a05c-107">This information is required so that the query can identify the style of paragraphs that don't have a style explicitly set.</span></span> <span data-ttu-id="5a05c-108">Paragraf stilleri öğe aracılığıyla ayarlanır `w:pPr` ; bir paragraf bu öğeyi içermiyorsa varsayılan stille biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5a05c-108">Paragraph styles are set through the `w:pPr` element; if a paragraph doesn't contain this element, it's formatted with the default style.</span></span>

<span data-ttu-id="5a05c-109">Bu makalede sorgunun bazı parçalarının önemi açıklanmakta ve ardından sorgu tam bir çalışma örneği kapsamında gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="5a05c-109">This article explains the significance of some pieces of the query, then shows the query as part of a complete working example.</span></span>

## <a name="example-retrieve-all-the-paragraphs-in-a-document-and-the-paragraph-styles"></a><span data-ttu-id="5a05c-110">Örnek: bir belgedeki tüm paragrafları ve paragraf stillerini alma</span><span class="sxs-lookup"><span data-stu-id="5a05c-110">Example: Retrieve all the paragraphs in a document, and the paragraph styles</span></span>

<span data-ttu-id="5a05c-111">Aşağıdaki kod, bir belgedeki tüm paragrafları ve stillerini almak için bir sorgudur:</span><span class="sxs-lookup"><span data-stu-id="5a05c-111">The following code is a query to retrieve all the paragraphs in a document and their styles:</span></span>

```csharp
xDoc.Root.Element(w + "body").Descendants(w + "p")
```

```vb
xDoc.Root.<w:body>...<w:p>
```

<span data-ttu-id="5a05c-112">Bu ifade, önceki örnekteki sorgunun kaynağına benzer, [varsayılan paragraf stilini bulur](find-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="5a05c-112">This expression is similar to the source of the query in the previous example, [Find the default paragraph style](find-default-paragraph-style.md).</span></span> <span data-ttu-id="5a05c-113">Temel fark, <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yerine eksenin kullanıldığı bir değer <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="5a05c-113">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="5a05c-114">Sorgu, bölümleri bulunan <xref:System.Xml.Linq.XContainer.Descendants%2A> belgelerde, paragrafları gövde öğesinin doğrudan alt öğeleri olmayacak şekilde kullanır. bunun yerine, paragraflar hiyerarşide iki düzey olur.</span><span class="sxs-lookup"><span data-stu-id="5a05c-114">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs won't be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="5a05c-115"><xref:System.Xml.Linq.XContainer.Descendants%2A>Eksen kullanılarak, kod belgenin bölüm kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a05c-115">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work whether or not the document uses sections.</span></span>

## <a name="example-use-a-let-clause-to-determine-the-element-that-contains-the-style-node"></a><span data-ttu-id="5a05c-116">Örnek: `let` Stil düğümünü içeren öğeyi belirlemede bir yan tümce kullanın</span><span class="sxs-lookup"><span data-stu-id="5a05c-116">Example: Use a `let` clause to determine the element that contains the style node</span></span>

<span data-ttu-id="5a05c-117">Aşağıdaki sorgu, `let` Stil düğümünü içeren öğeyi tespit etmek için bir yan tümce kullanır:</span><span class="sxs-lookup"><span data-stu-id="5a05c-117">The following query uses a `let` clause to determine the element that contains the style node:</span></span>

```csharp
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()
```

 ```vb
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()
```

<span data-ttu-id="5a05c-118">`let`Yan tümcesi ( `Let` Visual Basic sürümünde), ilk olarak <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksenini kullanır `pPr` , ardından <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemini kullanır `pStyle` ve son olarak, <xref:System.Linq.Enumerable.FirstOrDefault%2A> koleksiyonu tek bir olarak dönüştürmek için standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a05c-118">The `let` clause (`Let` in the Visual Basic version) first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="5a05c-119">Koleksiyon boşsa, `styleNode` `null` ( `Nothing` Visual Basic sürümünde) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5a05c-119">If the collection is empty, `styleNode` is set to `null` (`Nothing` in the Visual Basic version).</span></span> <span data-ttu-id="5a05c-120">Bu, alt düğümü aramak için kullanışlı bir deyimdir `pStyle` .</span><span class="sxs-lookup"><span data-stu-id="5a05c-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="5a05c-121">`pPr`Alt düğüm yoksa, kod bir özel durum oluşturarak başarısız olmaz, bunun yerine, `styleNode` `null` `Nothing` Bu `let` ( `Let` ) yan tümcesinin istenen davranışı olan () olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5a05c-121">Note that if the `pPr` child node doesn't exist, the code doesn't fail by throwing an exception; instead, `styleNode` is set to `null` (`Nothing`), which is the desired behavior of this `let`(`Let`) clause.</span></span>

<span data-ttu-id="5a05c-122">Öğe yoksa, `styleNode` `null` () olarak ayarlanır `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5a05c-122">If there is no element, then `styleNode` is set to `null` (`Nothing`).</span></span>

<span data-ttu-id="5a05c-123">Sorgu, iki üyeli anonim bir türün bir koleksiyonunu `StyleName` ve `ParagraphNode` .</span><span class="sxs-lookup"><span data-stu-id="5a05c-123">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>

## <a name="example-retrieve-the-paragraph-nodes-from-a-wordprocessingml-document"></a><span data-ttu-id="5a05c-124">Örnek: bir WordprocessingML belgesinden paragraf düğümlerini alma</span><span class="sxs-lookup"><span data-stu-id="5a05c-124">Example: Retrieve the paragraph nodes from a WordprocessingML document</span></span>

<span data-ttu-id="5a05c-125">Bu örnekte, paragraf düğümlerini alarak bir WordprocessingML belgesi işlenir.</span><span class="sxs-lookup"><span data-stu-id="5a05c-125">This example processes a WordprocessingML document, retrieving the paragraph nodes.</span></span> <span data-ttu-id="5a05c-126">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="5a05c-126">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="5a05c-127">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="5a05c-127">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="5a05c-128">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5a05c-128">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="5a05c-129">Bu örnek için kaynak belge oluşturmaya yönelik yönergeler, [kaynak Office Open XML belgesini oluşturma](create-source-office-open-xml-document.md)' da bulunur.</span><span class="sxs-lookup"><span data-stu-id="5a05c-129">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="5a05c-130">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a05c-130">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="5a05c-131"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a05c-131">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
const string fileName = "SampleDoc.docx";

const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
XNamespace w = wordmlNamespace;

XDocument xDoc = null;
XDocument styleDoc = null;

using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
{
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
    if (docPackageRelationship != null)
    {
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);
        PackagePart documentPart = wdPackage.GetPart(documentUri);

        //  Load the document XML in the part into an XDocument instance.
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

        //  Find the styles part. There will only be one.
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
        if (styleRelation != null)
        {
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
            PackagePart stylePart = wdPackage.GetPart(styleUri);

            //  Load the style XML in the part into an XDocument instance.
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
        }
    }
}

string defaultStyle =
    (string)(
        from style in styleDoc.Root.Elements(w + "style")
        where (string)style.Attribute(w + "type") == "paragraph"&&
              (string)style.Attribute(w + "default") == "1"
              select style
    ).First().Attribute(w + "styleId");

// Following is the new query that finds all paragraphs in the
// document and their styles.
var paragraphs =
    from para in xDoc
                 .Root
                 .Element(w + "body")
                 .Descendants(w + "p")
    let styleNode = para
                    .Elements(w + "pPr")
                    .Elements(w + "pStyle")
                    .FirstOrDefault()
    select new
    {
        ParagraphNode = para,
        StyleName = styleNode != null ?
            (string)styleNode.Attribute(w + "val") :
            defaultStyle
    };

foreach (var p in paragraphs)
    Console.WriteLine("StyleName:{0}", p.StyleName);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    '  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        Dim defaultStyle As String = _
            ( _
                From style In styleDoc.Root.<w:style> _
                Where style.@w:type = "paragraph" And _
                      style.@w:default = "1" _
                Select style _
            ).First().@w:styleId

        ' Following is the new query that finds all paragraphs in the
        ' document and their styles.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        For Each p In paragraphs
            Console.WriteLine("StyleName:{0}", p.StyleName)
        Next

    End Sub
End Module
```

<span data-ttu-id="5a05c-132">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5a05c-132">This example produces the following output:</span></span>

```output
StyleName:Heading1
StyleName:Normal
StyleName:Normal
StyleName:Normal
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Normal
StyleName:Normal
StyleName:Normal
StyleName:Code
```

<span data-ttu-id="5a05c-133">Bu öğreticideki sonraki makalede, paragrafların metnini almak için bir sorgu oluşturma gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5a05c-133">The next article in this tutorial shows how to create a query to retrieve the text of paragraphs:</span></span>

- [<span data-ttu-id="5a05c-134">Paragrafların metnini alma</span><span class="sxs-lookup"><span data-stu-id="5a05c-134">Retrieve the text of the paragraphs</span></span>](retrieve-text-paragraphs.md)

## <a name="see-also"></a><span data-ttu-id="5a05c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a05c-135">See also</span></span>

- [<span data-ttu-id="5a05c-136">Öğretici: WordprocessingML belgesinde içerik Işleme</span><span class="sxs-lookup"><span data-stu-id="5a05c-136">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)

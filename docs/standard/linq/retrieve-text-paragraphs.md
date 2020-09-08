---
title: Paragrafların metnini al-LINQ to XML
description: Bir WordprocessingML belgesinde paragraf düğümlerini bulmayı ve her düğümden bir dize olarak metin almayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: f41e0206f91f022993ed2c48681f124bf84ec603
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553646"
---
# <a name="retrieve-the-text-of-the-paragraphs-linq-to-xml"></a><span data-ttu-id="fdf2b-103">Paragrafların metnini al (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fdf2b-103">Retrieve the text of the paragraphs (LINQ to XML)</span></span>

<span data-ttu-id="fdf2b-104">Bu örnek, önceki örnekte yer alan, [paragrafları ve stillerini alır](retrieve-paragraphs-styles.md).</span><span class="sxs-lookup"><span data-stu-id="fdf2b-104">This example builds on the previous example, [Retrieve the paragraphs and their styles](retrieve-paragraphs-styles.md).</span></span> <span data-ttu-id="fdf2b-105">Bu yeni örnek, her bir paragrafın metnini dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-105">This new example retrieves the text of each paragraph as a string.</span></span>

<span data-ttu-id="fdf2b-106">Bu örnek, metni almak için anonim türler koleksiyonu ve proje, yeni bir üyenin eklenmesiyle anonim bir türün yeni bir koleksiyonu aracılığıyla yinelenen ek bir sorgu ekler `Text` .</span><span class="sxs-lookup"><span data-stu-id="fdf2b-106">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="fdf2b-107"><xref:System.Linq.Enumerable.Aggregate%2A>Birden çok dizeyi tek bir dizede birleştirmek için standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-107">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>

<span data-ttu-id="fdf2b-108">Bu teknik (yani, ilk olarak anonim bir türün koleksiyonuna yansıtırken, daha sonra bu koleksiyonun yeni bir anonim tür koleksiyonuna proje için kullanılması) ortak ve kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-108">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful one.</span></span> <span data-ttu-id="fdf2b-109">Bu sorgu, ilk anonim türe yansıtılamadan yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-109">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="fdf2b-110">Ancak, yavaş değerlendirme nedeniyle bunu yapmak çok daha fazla işlem gücü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-110">However, because of lazy evaluation, doing so doesn't use much additional processing power.</span></span> <span data-ttu-id="fdf2b-111">Teknik, yığında daha kısa ömürlü nesneler oluşturur, ancak performansı önemli ölçüde düşürür.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-111">The technique does create more short-lived objects on the heap, but that doesn't substantially degrade performance.</span></span>

<span data-ttu-id="fdf2b-112">Tabii ki, paragrafları alma işlevini, her bir paragrafın stilini ve her bir paragrafın metnini içeren tek bir sorgu yazmak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-112">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="fdf2b-113">Ancak, sonuçta elde edilen kod daha modüler ve bakım açısından daha kolay olduğundan, daha karmaşık bir sorguyu birden çok sorguya bölmek genellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-113">However, it's often useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="fdf2b-114">Ayrıca, sorgunun bir bölümünü yeniden kullanmanız gerekiyorsa, sorgular bu şekilde yazılmışsa, yeniden düzenleme daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-114">Further, if you need to reuse a portion of the query, it's easier to refactor if the queries are written in this manner.</span></span>

<span data-ttu-id="fdf2b-115">Birlikte zincirleme olan bu sorgular, makale [zinciri sorguları örneğinde](chain-queries-example.md)incelenen işleme modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-115">These queries, which are chained together, use the processing model that's examined in the article [Chain queries example](chain-queries-example.md).</span></span>

## <a name="example-determine-the-element-node-style-name-and-text-of-each-paragraph"></a><span data-ttu-id="fdf2b-116">Örnek: öğe düğümünü, stil adını ve her bir paragrafın metnini belirleme</span><span class="sxs-lookup"><span data-stu-id="fdf2b-116">Example: Determine the element node, style name, and text of each paragraph</span></span>

<span data-ttu-id="fdf2b-117">Bu örnek, her bir paragrafın öğe düğümünü, stil adını ve metnini belirleyen bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-117">This example processes a WordprocessingML document, determining the element node, style name, and text of each paragraph.</span></span> <span data-ttu-id="fdf2b-118">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-118">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="fdf2b-119">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-119">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="fdf2b-120">Bu örnek için kaynak belge oluşturmaya yönelik yönergeler, [kaynak Office Open XML belgesini oluşturma](create-source-office-open-xml-document.md)' da bulunur.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-120">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="fdf2b-121">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-121">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="fdf2b-122"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-122">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
const string fileName = "SampleDoc.docx";

const string documentRelationshipType =
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
const string stylesRelationshipType =
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
const string wordmlNamespace =
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
XNamespace w = wordmlNamespace;

XDocument xDoc = null;
XDocument styleDoc = null;

using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
{
    PackageRelationship docPackageRelationship =
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
    if (docPackageRelationship != null)
    {
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),
          docPackageRelationship.TargetUri);
        PackagePart documentPart = wdPackage.GetPart(documentUri);

        //  Load the document XML in the part into an XDocument instance.
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

        //  Find the styles part. There will only be one.
        PackageRelationship styleRelation =
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
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

// Find all paragraphs in the document.
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

// Following is the new query that retrieves the text of
// each paragraph.
var paraWithText =
    from para in paragraphs
    select new
    {
        ParagraphNode = para.ParagraphNode,
        StyleName = para.StyleName,
        Text = para
               .ParagraphNode
               .Elements(w + "r")
               .Elements(w + "t")
               .Aggregate(
                   new StringBuilder(),
                   (s, i) => s.Append((string)i),
                   s => s.ToString()
               )
    };

foreach (var p in paraWithText)
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    ' Following function is required because Visual Basic doesn't support short circuit evaluation
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _
                                         ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = _
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = _
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _
                  docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = _
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = _
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
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

        ' Find all paragraphs in the document.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        ' Following is the new query that retrieves the text of
        ' each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = para.ParagraphNode.<w:r>.<w:t> _
                    .Aggregate(New StringBuilder(), _
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _
                               Function(s As StringBuilder) s.ToString) _
            }

        For Each p In paraWithText
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next

    End Sub
End Module
```

<span data-ttu-id="fdf2b-123">Bu örneğin C# sürümü aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fdf2b-123">The C# version of this example produces the following output:</span></span>

```conssole
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<
StyleName:Normal ><
StyleName:Normal >The following example prints to the console.<
StyleName:Normal ><
StyleName:Code >using System;<
StyleName:Code ><
StyleName:Code >class Program {<
StyleName:Code >    public static void (string[] args) {<
StyleName:Code >        Console.WriteLine("Hello World");<
StyleName:Code >    }<
StyleName:Code >}<
StyleName:Normal ><
StyleName:Normal >This example produces the following output:<
StyleName:Normal ><
StyleName:Code >Hello World<
```

<span data-ttu-id="fdf2b-124">Bu örneğin Visual Basic sürümü aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fdf2b-124">The Visual Basic version of this example produces the following output:</span></span>

```output
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<
StyleName:Normal ><
StyleName:Normal >The following example prints to the console.<
StyleName:Normal ><
StyleName:Code >Imports System<
StyleName:Code ><
StyleName:Code >Class Program<
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<
StyleName:Code >        Console.WriteLine("Hello World")<
StyleName:Code >   End Sub<
StyleName:Code >End Class<
StyleName:Normal ><
StyleName:Normal >This example produces the following output:<
StyleName:Normal ><
StyleName:Code >Hello World<
```

<span data-ttu-id="fdf2b-125">Bu öğreticideki Sonraki Makale, <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi tek bir dizeye birleştirmek için yerine bir genişletme yönteminin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="fdf2b-125">The next article in this tutorial shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string:</span></span>

- [<span data-ttu-id="fdf2b-126">Genişletme yöntemi kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="fdf2b-126">Refactor using an extension method</span></span>](refactor-extension-method.md)

## <a name="see-also"></a><span data-ttu-id="fdf2b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdf2b-127">See also</span></span>

- [<span data-ttu-id="fdf2b-128">Öğretici: WordprocessingML belgesinde içerik Işleme</span><span class="sxs-lookup"><span data-stu-id="fdf2b-128">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="fdf2b-129">Ertelenmiş yürütme ve geç değerlendirme</span><span class="sxs-lookup"><span data-stu-id="fdf2b-129">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)

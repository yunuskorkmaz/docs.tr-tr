---
title: Varsayılan paragraf stilini bulun-LINQ to XML
description: WordprocessingML belgesinde paragrafların varsayılan stilini bulmayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 0e66856a551410dd488148ff678b684489396d62
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552901"
---
# <a name="find-the-default-paragraph-style-linq-to-xml"></a><span data-ttu-id="e93bb-103">Varsayılan paragraf stilini bul (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e93bb-103">Find the default paragraph style (LINQ to XML)</span></span>

<span data-ttu-id="e93bb-104">Öğreticideki ilk görev [: WordprocessingML belgesinde Içerik işleme](xml-shape-wordprocessingml-documents.md) , belgede varsayılan paragraf stilini bullevidir.</span><span class="sxs-lookup"><span data-stu-id="e93bb-104">The first task in [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) is to find the default style of paragraphs in the document.</span></span>

## <a name="example-find-the-default-style-name"></a><span data-ttu-id="e93bb-105">Örnek: varsayılan stil adını bulun</span><span class="sxs-lookup"><span data-stu-id="e93bb-105">Example: Find the default style name</span></span>

<span data-ttu-id="e93bb-106">Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paketin belge ve stil parçalarını bulur ve ardından varsayılan stil adını bulan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="e93bb-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="e93bb-107">Office Open XML belge paketleri ve içerdikleri parçalar hakkında daha fazla bilgi için bkz. [Office Open XML WordprocessingML belgelerinin ayrıntıları](wordprocessingml-document-styles.md).</span><span class="sxs-lookup"><span data-stu-id="e93bb-107">For information about Office Open XML document packages, and the parts they comprise, see [Details of Office Open XML WordprocessingML documents](wordprocessingml-document-styles.md).</span></span>

<span data-ttu-id="e93bb-108">Sorgu, "paragraf" değeri ile adlandırılmış bir özniteliği olan adlı bir düğümü bulur `w:style` `w:type` ve ayrıca `w:default` "1" değerine sahip adlı bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e93bb-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="e93bb-109">Bu özniteliklere sahip yalnızca bir XML düğümü olacağı için, sorgu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> işleci kullanarak bir koleksiyonu tek bir öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e93bb-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="e93bb-110">Daha sonra, adlı özniteliğin değerini alır `w:styleId` .</span><span class="sxs-lookup"><span data-stu-id="e93bb-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>

<span data-ttu-id="e93bb-111">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e93bb-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="e93bb-112"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="e93bb-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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

// The following query finds all the paragraphs that have the default style.
string defaultStyle =
    (string)(
        from style in styleDoc.Root.Elements(w + "style")
        where (string)style.Attribute(w + "type") == "paragraph"&&
              (string)style.Attribute(w + "default") == "1"
              select style
    ).First().Attribute(w + "styleId");

Console.WriteLine("The default style is: {0}", defaultStyle);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1

    Sub Main()

        Const fileName As String = "SampleDoc.docx"

        Const documentRelationshipType As String = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Const stylesRelationshipType As String = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = _
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If docPackageRelationship IsNot Nothing Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _
                  docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                ' Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                ' Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = _
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If styleRelation IsNot Nothing Then
                    Dim styleUri As Uri = _
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    ' Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        ' The following query finds all the paragraphs that have the default style.
        Dim defParas As IEnumerable(Of XElement) = _
            From style In styleDoc.Root.<w:style> _
            Where style.@w:type.Equals("paragraph") And _
                   style.@w:default.Equals("1") _
            Select style
        ' Then find the style of the first.
        Dim defaultStyle As String = defParas.First().@w:styleId

        Console.WriteLine("The default style is: " & defaultStyle)
    End Sub
End Module
```

<span data-ttu-id="e93bb-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e93bb-113">This example produces the following output:</span></span>

```output
The default style is: Normal
```

<span data-ttu-id="e93bb-114">Bu öğreticideki bir sonraki makalede, bir belgedeki tüm paragrafları ve bunların stillerini bulan benzer bir sorgu oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="e93bb-114">In the next article in this tutorial you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>

- [<span data-ttu-id="e93bb-115">Paragrafları ve stillerini alma</span><span class="sxs-lookup"><span data-stu-id="e93bb-115">Retrieve the paragraphs and their styles</span></span>](retrieve-paragraphs-styles.md)

## <a name="see-also"></a><span data-ttu-id="e93bb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e93bb-116">See also</span></span>

- [<span data-ttu-id="e93bb-117">Öğretici: WordprocessingML belgesinde içerik Işleme</span><span class="sxs-lookup"><span data-stu-id="e93bb-117">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)

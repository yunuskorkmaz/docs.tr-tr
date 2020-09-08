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
# <a name="find-the-default-paragraph-style-linq-to-xml"></a>Varsayılan paragraf stilini bul (LINQ to XML)

Öğreticideki ilk görev [: WordprocessingML belgesinde Içerik işleme](xml-shape-wordprocessingml-documents.md) , belgede varsayılan paragraf stilini bullevidir.

## <a name="example-find-the-default-style-name"></a>Örnek: varsayılan stil adını bulun

Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paketin belge ve stil parçalarını bulur ve ardından varsayılan stil adını bulan bir sorgu yürütür. Office Open XML belge paketleri ve içerdikleri parçalar hakkında daha fazla bilgi için bkz. [Office Open XML WordprocessingML belgelerinin ayrıntıları](wordprocessingml-document-styles.md).

Sorgu, "paragraf" değeri ile adlandırılmış bir özniteliği olan adlı bir düğümü bulur `w:style` `w:type` ve ayrıca `w:default` "1" değerine sahip adlı bir özniteliğe sahiptir. Bu özniteliklere sahip yalnızca bir XML düğümü olacağı için, sorgu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> işleci kullanarak bir koleksiyonu tek bir öğesine dönüştürür. Daha sonra, adlı özniteliğin değerini alır `w:styleId` .

Bu örnek, WindowsBase derlemesinden sınıfları kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
The default style is: Normal
```

Bu öğreticideki bir sonraki makalede, bir belgedeki tüm paragrafları ve bunların stillerini bulan benzer bir sorgu oluşturacaksınız:

- [Paragrafları ve stillerini alma](retrieve-paragraphs-styles.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesinde içerik Işleme](xml-shape-wordprocessingml-documents.md)

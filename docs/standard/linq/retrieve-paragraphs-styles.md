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
# <a name="retrieve-the-paragraphs-and-their-styles-linq-to-xml"></a>Paragrafları ve stillerini alma (LINQ to XML)

Bu örnekte, bir WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazdık. Ayrıca her bir paragrafın stilini belirler.

Bu sorgu, önceki örnekteki sorgu üzerinde yapılar, varsayılan stili stil listesinden alan [varsayılan paragraf stilini bulur](find-default-paragraph-style.md). Bu bilgiler, sorgunun açıkça ayarlanmış bir stile sahip olmayan paragrafların stilini belirleyebilmesi için gereklidir. Paragraf stilleri öğe aracılığıyla ayarlanır `w:pPr` ; bir paragraf bu öğeyi içermiyorsa varsayılan stille biçimlendirilir.

Bu makalede sorgunun bazı parçalarının önemi açıklanmakta ve ardından sorgu tam bir çalışma örneği kapsamında gösteriliyor.

## <a name="example-retrieve-all-the-paragraphs-in-a-document-and-the-paragraph-styles"></a>Örnek: bir belgedeki tüm paragrafları ve paragraf stillerini alma

Aşağıdaki kod, bir belgedeki tüm paragrafları ve stillerini almak için bir sorgudur:

```csharp
xDoc.Root.Element(w + "body").Descendants(w + "p")
```

```vb
xDoc.Root.<w:body>...<w:p>
```

Bu ifade, önceki örnekteki sorgunun kaynağına benzer, [varsayılan paragraf stilini bulur](find-default-paragraph-style.md). Temel fark, <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yerine eksenin kullanıldığı bir değer <xref:System.Xml.Linq.XContainer.Elements%2A> . Sorgu, bölümleri bulunan <xref:System.Xml.Linq.XContainer.Descendants%2A> belgelerde, paragrafları gövde öğesinin doğrudan alt öğeleri olmayacak şekilde kullanır. bunun yerine, paragraflar hiyerarşide iki düzey olur. <xref:System.Xml.Linq.XContainer.Descendants%2A>Eksen kullanılarak, kod belgenin bölüm kullanıp kullanmadığını belirtir.

## <a name="example-use-a-let-clause-to-determine-the-element-that-contains-the-style-node"></a>Örnek: `let` Stil düğümünü içeren öğeyi belirlemede bir yan tümce kullanın

Aşağıdaki sorgu, `let` Stil düğümünü içeren öğeyi tespit etmek için bir yan tümce kullanır:

```csharp
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()
```

 ```vb
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()
```

`let`Yan tümcesi ( `Let` Visual Basic sürümünde), ilk olarak <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksenini kullanır `pPr` , ardından <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemini kullanır `pStyle` ve son olarak, <xref:System.Linq.Enumerable.FirstOrDefault%2A> koleksiyonu tek bir olarak dönüştürmek için standart sorgu işlecini kullanır. Koleksiyon boşsa, `styleNode` `null` ( `Nothing` Visual Basic sürümünde) olarak ayarlanır. Bu, alt düğümü aramak için kullanışlı bir deyimdir `pStyle` . `pPr`Alt düğüm yoksa, kod bir özel durum oluşturarak başarısız olmaz, bunun yerine, `styleNode` `null` `Nothing` Bu `let` ( `Let` ) yan tümcesinin istenen davranışı olan () olarak ayarlanır.

Öğe yoksa, `styleNode` `null` () olarak ayarlanır `Nothing` .

Sorgu, iki üyeli anonim bir türün bir koleksiyonunu `StyleName` ve `ParagraphNode` .

## <a name="example-retrieve-the-paragraph-nodes-from-a-wordprocessingml-document"></a>Örnek: bir WordprocessingML belgesinden paragraf düğümlerini alma

Bu örnekte, paragraf düğümlerini alarak bir WordprocessingML belgesi işlenir. Ayrıca her bir paragrafın stilini belirler. Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır. Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.

Bu örnek için kaynak belge oluşturmaya yönelik yönergeler, [kaynak Office Open XML belgesini oluşturma](create-source-office-open-xml-document.md)' da bulunur.

Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.

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

Bu örnek aşağıdaki çıktıyı üretir:

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

Bu öğreticideki sonraki makalede, paragrafların metnini almak için bir sorgu oluşturma gösterilmektedir:

- [Paragrafların metnini alma](retrieve-text-paragraphs.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesinde içerik Işleme](xml-shape-wordprocessingml-documents.md)

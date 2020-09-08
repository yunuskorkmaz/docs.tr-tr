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
# <a name="retrieve-the-text-of-the-paragraphs-linq-to-xml"></a>Paragrafların metnini al (LINQ to XML)

Bu örnek, önceki örnekte yer alan, [paragrafları ve stillerini alır](retrieve-paragraphs-styles.md). Bu yeni örnek, her bir paragrafın metnini dize olarak alır.

Bu örnek, metni almak için anonim türler koleksiyonu ve proje, yeni bir üyenin eklenmesiyle anonim bir türün yeni bir koleksiyonu aracılığıyla yinelenen ek bir sorgu ekler `Text` . <xref:System.Linq.Enumerable.Aggregate%2A>Birden çok dizeyi tek bir dizede birleştirmek için standart sorgu işlecini kullanır.

Bu teknik (yani, ilk olarak anonim bir türün koleksiyonuna yansıtırken, daha sonra bu koleksiyonun yeni bir anonim tür koleksiyonuna proje için kullanılması) ortak ve kullanışlı bir yöntemdir. Bu sorgu, ilk anonim türe yansıtılamadan yazılmış olabilir. Ancak, yavaş değerlendirme nedeniyle bunu yapmak çok daha fazla işlem gücü kullanmaz. Teknik, yığında daha kısa ömürlü nesneler oluşturur, ancak performansı önemli ölçüde düşürür.

Tabii ki, paragrafları alma işlevini, her bir paragrafın stilini ve her bir paragrafın metnini içeren tek bir sorgu yazmak mümkün olacaktır. Ancak, sonuçta elde edilen kod daha modüler ve bakım açısından daha kolay olduğundan, daha karmaşık bir sorguyu birden çok sorguya bölmek genellikle yararlı olur. Ayrıca, sorgunun bir bölümünü yeniden kullanmanız gerekiyorsa, sorgular bu şekilde yazılmışsa, yeniden düzenleme daha kolay olur.

Birlikte zincirleme olan bu sorgular, makale [zinciri sorguları örneğinde](chain-queries-example.md)incelenen işleme modelini kullanır.

## <a name="example-determine-the-element-node-style-name-and-text-of-each-paragraph"></a>Örnek: öğe düğümünü, stil adını ve her bir paragrafın metnini belirleme

Bu örnek, her bir paragrafın öğe düğümünü, stil adını ve metnini belirleyen bir WordprocessingML belgesini işler. Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır. Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.

Bu örnek için kaynak belge oluşturmaya yönelik yönergeler, [kaynak Office Open XML belgesini oluşturma](create-source-office-open-xml-document.md)' da bulunur.

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

Bu örneğin C# sürümü aşağıdaki çıktıyı üretir:

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

Bu örneğin Visual Basic sürümü aşağıdaki çıktıyı üretir:

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

Bu öğreticideki Sonraki Makale, <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi tek bir dizeye birleştirmek için yerine bir genişletme yönteminin nasıl kullanılacağını gösterir:

- [Genişletme yöntemi kullanarak yeniden düzenleme](refactor-extension-method.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesinde içerik Işleme](xml-shape-wordprocessingml-documents.md)
- [Ertelenmiş yürütme ve geç değerlendirme](deferred-execution-lazy-evaluation.md)

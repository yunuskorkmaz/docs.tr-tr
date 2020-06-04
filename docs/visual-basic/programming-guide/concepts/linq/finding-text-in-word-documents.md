---
title: Word Belgelerinde Metin Bulma
ms.date: 07/20/2015
ms.assetid: eea9819b-a78a-4552-bf13-8837fc0e7a37
ms.openlocfilehash: 546703e3dbead64fd10c04fe52cb1dd98ba53049
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398096"
---
# <a name="finding-text-in-word-documents-visual-basic"></a><span data-ttu-id="1dc38-102">Word belgelerinde metin bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dc38-102">Finding Text in Word Documents (Visual Basic)</span></span>

<span data-ttu-id="1dc38-103">Bu konu, bir şeyi yararlı yapmak için önceki sorguları genişletir: belgede bir dizenin tüm yinelemelerini bulur.</span><span class="sxs-lookup"><span data-stu-id="1dc38-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>

## <a name="example"></a><span data-ttu-id="1dc38-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1dc38-104">Example</span></span>

<span data-ttu-id="1dc38-105">Bu örnek, belgedeki belirli bir metin parçasının tüm oluşumlarını bulmak için bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="1dc38-105">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="1dc38-106">Bunu yapmak için "Merhaba" dizesini bulan bir sorgu kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="1dc38-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="1dc38-107">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="1dc38-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="1dc38-108">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1dc38-108">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="1dc38-109">Bu örnek için kaynak belge oluşturmaya ilişkin yönergeler için bkz. [kaynak Office Open XML belgesi oluşturma (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="1dc38-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="1dc38-110">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1dc38-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="1dc38-111"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1dc38-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As String In source
            sb.Append(s)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item))
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As T In source
            sb.Append(s).Append(separator)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String), ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item)).Append(separator)
        Next
        Return sb.ToString()
    End Function

    Public Function ParagraphText(ByVal e As XElement) As String
        Dim w As XNamespace = e.Name.Namespace
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))
    End Function

    ' Following function is required because Visual Basic does not support short circuit evaluation
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

        ' Find all paragraphs in the document.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        ' Retrieve the text of each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = ParagraphText(para.ParagraphNode) _
            }

        ' Following is the new query that retrieves all paragraphs
        ' that have specific text in them.
        Dim helloParagraphs = _
            From para In paraWithText _
            Where para.Text.Contains("Hello") _
            Select New With _
            { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = para.Text _
            }

        For Each p In helloParagraphs
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next
    End Sub
End Module
```

<span data-ttu-id="1dc38-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1dc38-112">This example produces the following output:</span></span>

```console
StyleName:Code >        Console.WriteLine("Hello World")<
StyleName:Code >Hello World<
```

<span data-ttu-id="1dc38-113">Tabii ki, belirli bir stille satırları arayacak şekilde aramayı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1dc38-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="1dc38-114">Aşağıdaki sorgu, kod stiline sahip olan tüm boş satırları bulur:</span><span class="sxs-lookup"><span data-stu-id="1dc38-114">The following query finds all blank lines that have the Code style:</span></span>

```vb
Imports System.IO.Packaging
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As String In source
            sb.Append(s)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item))
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As T In source
            sb.Append(s).Append(separator)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String), ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item)).Append(separator)
        Next
        Return sb.ToString()
    End Function

    Public Function ParagraphText(ByVal e As XElement) As String
        Dim w As XNamespace = e.Name.Namespace
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))
    End Function

    ' Following function is required because Visual Basic does not support short circuit evaluation
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

        ' Find all paragraphs in the document.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        ' Retrieve the text of each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = ParagraphText(para.ParagraphNode) _
            }

        ' Retrieve all paragraphs that have no text and are styled Code.
        Dim blankCodeParagraphs = _
            From para In paraWithText _
            Where String.IsNullOrEmpty(para.Text) And para.StyleName.Equals("Code") _
            Select New With _
            { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = para.Text _
            }

        For Each p In blankCodeParagraphs
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next
    End Sub
End Module
```

<span data-ttu-id="1dc38-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1dc38-115">This example produces the following output:</span></span>

```console
StyleName:Code ><
```

<span data-ttu-id="1dc38-116">Tabii ki bu örnek çeşitli yollarla iyileştirilen olabilir.</span><span class="sxs-lookup"><span data-stu-id="1dc38-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="1dc38-117">Örneğin, normal ifadeleri metin aramak için kullanabiliriz, belirli bir dizindeki tüm Word dosyaları üzerinde yineliyoruz ve bu şekilde devam ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="1dc38-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>

<span data-ttu-id="1dc38-118">Bu örneğin, tek bir sorgu olarak yazılıp yazılmadığını ve bunun yaklaşık olarak gerçekleştiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1dc38-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="1dc38-119">Her sorgu geç, ertelenmiş bir biçimde uygulandığından, sorgu yinelenene kadar her sorgu kendi sonuçlarını vermez.</span><span class="sxs-lookup"><span data-stu-id="1dc38-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="1dc38-120">Yürütme ve yavaş değerlendirme hakkında daha fazla bilgi için bkz. [LINQ to XML ertelenmiş yürütme ve yavaş değerlendirme (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1dc38-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1dc38-121">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="1dc38-121">Next Steps</span></span>

<span data-ttu-id="1dc38-122">Sonraki bölümde WordprocessingML belgeleri hakkında daha fazla bilgi verilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1dc38-122">The next section provides more information about WordprocessingML documents:</span></span>

- [<span data-ttu-id="1dc38-123">Office Open XML WordprocessingML belgelerinin ayrıntıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dc38-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)

## <a name="see-also"></a><span data-ttu-id="1dc38-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dc38-124">See also</span></span>

- [<span data-ttu-id="1dc38-125">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dc38-125">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="1dc38-126">Saf Işlev kullanarak yeniden düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dc38-126">Refactoring Using a Pure Function (Visual Basic)</span></span>](refactoring-using-a-pure-function.md)
- [<span data-ttu-id="1dc38-127">LINQ to XML ertelenmiş yürütme ve geç değerlendirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dc38-127">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

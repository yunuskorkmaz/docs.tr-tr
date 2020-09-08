---
title: Uzantı yöntemi kullanarak yeniden düzenleme-LINQ to XML
description: Bir uzantı yöntemi olarak uygulanan bir saf işlev kullanarak dizelerin nasıl yeniden oluşturulduğunu öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: ea33bce2f534bce9e97d467c71df8a9474bbf6cd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553933"
---
# <a name="refactor-using-an-extension-method-linq-to-xml"></a>Genişletme yöntemi kullanarak yeniden düzenleme (LINQ to XML)

Bu örnek, bir uzantı yöntemi olarak uygulanan bir saf işlev kullanarak dizelerin birleştirilmesiyle yeniden düzenleyerek [paragrafın metnini alma](retrieve-text-paragraphs.md), önceki örnekte oluşturulur.

Önceki örnek, <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi tek bir dizede birleştirmek için standart sorgu işlecini kullandı. Bununla birlikte, bunu yapmak için bir genişletme yöntemi yazmak daha kolaydır çünkü sonuçta elde edilen sorgu daha küçük ve daha basittir.

## <a name="example-retrieve-the-paragraphs-their-styles-and-their-text"></a>Örnek: paragrafları, stillerini ve bunların metinlerini alın

Bu örnek, her bir paragrafın paragraflarını ve stilini ve metnini alarak bir WordprocessingML belgesini işler. Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.

Örnek, yönteminin birden çok aşırı yüklerini içerir `StringConcatenate` .

Bu örnek için kaynak belge oluşturmaya yönelik yönergeler, [kaynak Office Open XML belgesini oluşturma](create-source-office-open-xml-document.md)' da bulunur.

Bu örnek, WindowsBase derlemesinden sınıfları kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.

```csharp
public static class LocalExtensions
{
    public static string StringConcatenate(this IEnumerable<string> source)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item));
        return sb.ToString();
    }

    public static string StringConcatenate(this IEnumerable<string> source, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s).Append(separator);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item)).Append(separator);
        return sb.ToString();
    }
}
```

```vb
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
```

## <a name="example-use-all-four-overloads-of-the-stringconcatenate-method"></a>Örnek: yöntemin dört aşırı yüklemesini kullanın `StringConcatenate`

Metodun dört aşırı yüklemesi vardır `StringConcatenate` . Bir aşırı yükleme yalnızca bir dize koleksiyonu alır ve tek bir dize döndürür. Başka bir aşırı yükleme, herhangi bir türün bir koleksiyonunu ve bir koleksiyonun tek bir sınıfından bir dizeye olan bir temsilciyi alabilir. Bir ayırıcı dize belirtmenizi sağlayan iki aşırı yükleme daha vardır.

Aşağıdaki kod dört aşırı yüklemeyi kullanır:

```csharp
string[] numbers = { "one", "two", "three" };

Console.WriteLine("{0}", numbers.StringConcatenate());
Console.WriteLine("{0}", numbers.StringConcatenate(":"));

int[] intNumbers = { 1, 2, 3 };
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));
```

```vb
Dim numbers As String() = {"one", "two", "three"}

Console.WriteLine("{0}", numbers.StringConcatenate())
Console.WriteLine("{0}", numbers.StringConcatenate(":"))

Dim intNumbers As Integer() = {1, 2, 3}
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString()))
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString(), ":"))
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
onetwothree
one:two:three:
123
1:2:3:
```

## <a name="example-use-the-new-extension-method"></a>Örnek: New Extension metodunu kullanın

Şimdi örnek, yeni uzantı yönteminden faydalanmak için değiştirilebilir:

```csharp
public static class LocalExtensions
{
    public static string StringConcatenate(this IEnumerable<string> source)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item));
        return sb.ToString();
    }

    public static string StringConcatenate(this IEnumerable<string> source, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s).Append(separator);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item)).Append(separator);
        return sb.ToString();
    }
}

class Program
{
    static void Main(string[] args)
    {
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
                    Uri styleUri =
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
                    PackagePart stylePart = wdPackage.GetPart(styleUri);

                    //  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
                }
            }
        }

        string defaultStyle =
            (string)(
                from style in styleDoc.Root.Elements(w + "style")
                where (string)style.Attribute(w + "type") == "paragraph" &&
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

        // Retrieve the text of each paragraph.
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
                       .StringConcatenate(e => (string)e)
            };

        foreach (var p in paraWithText)
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);
    }
}
```

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

        ' Retrieve the text of each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = para.ParagraphNode.<w:r>.<w:t>.StringConcatenate(Function(e) CStr(e)) _
            }

        For Each p In paraWithText
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next

    End Sub
End Module
```

 Bu örnek aşağıdaki çıktıyı üretir:

```output
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

Bu yeniden düzenleme, saf bir işleve yeniden düzenleme çeşidine sahiptir. Bu öğreticideki sonraki makalede, bu kodu saf işlevlerde yeniden düzenleme hakkında daha ayrıntılı bilgi verilmektedir:

- [Saf işlev kullanarak yeniden düzenleme](refactor-pure-function.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesinde içerik Işleme](xml-shape-wordprocessingml-documents.md)
- [Saf işlevlerde yeniden düzenleme](refactor-pure-functions.md)

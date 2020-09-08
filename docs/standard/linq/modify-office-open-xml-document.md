---
title: Office Open XML belgesini değiştirme-LINQ to XML
description: Bu makalede, bir Office Open XML belgesi açan, değiştiren ve kaydeden C# ve Visual Basic için bir örnek sunulmaktadır.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 467d489c-2b1b-453b-a757-8ac180e82a96
ms.openlocfilehash: 03cf760a7d591e9aa2f05007be299502581e4e2a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553147"
---
# <a name="how-to-modify-an-office-open-xml-document-linq-to-xml"></a>Office Open XML belgesini değiştirme (LINQ to XML)

Bu makalede, bir Office Open XML belgesi açan, değiştiren ve kaydeden C# ve Visual Basic için bir örnek sunulmaktadır.

Office Open XML hakkında daha fazla bilgi için bkz. [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) ve [www.ericwhite.com](http://ericwhite.com/).

## <a name="example"></a>Örnek

Bu örnek belgedeki ilk paragraf öğesini bulur. Metni paragrafdan alır ve tüm metin çalıştırmalarını siler. Büyük harfe dönüştürülen ilk paragrafın metinden oluşan yeni bir metin çalıştırması oluşturur. Daha sonra değiştirilmiş XML 'i Open XML paketine serileştirir ve kapatır.

Örnek, [kaynak Office Open XML belgesi oluşturma](create-source-office-open-xml-document.md)bölümünde açıklanan OFFICE Open XML belgesi üzerinde çalışır.

Şunları kullanır:

- `StringConcatenate`Örneğin bir parçası olarak tanımlanan genişletme yöntemi.
- WindowsBase derlemesinde bulunan sınıflar.
- <xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türler.

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
    public static string ParagraphText(XElement e)
    {
        XNamespace w = e.Name.Namespace;
        return e
               .Elements(w + "r")
               .Elements(w + "t")
               .StringConcatenate(element => (string)element);
    }

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

        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite))
        {
            PackageRelationship docPackageRelationship =
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
            if (docPackageRelationship != null)
            {
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),
                  docPackageRelationship.TargetUri);
                PackagePart documentPart = wdPackage.GetPart(documentUri);

                //  Load the document XML in the part into an XDocument instance.
                XDocument xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

                //  Find the styles part. There will only be one.
                PackageRelationship styleRelation =
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
                PackagePart stylePart = null;
                XDocument styleDoc = null;

                if (styleRelation != null)
                {
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
                    stylePart = wdPackage.GetPart(styleUri);

                    //  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
                }

                XElement paraNode = xDoc
                                    .Root
                                    .Element(w + "body")
                                    .Descendants(w + "p")
                                    .FirstOrDefault();

                string paraText = ParagraphText(paraNode);

                // remove all text runs
                paraNode.Descendants(w + "r").Remove();

                paraNode.Add(
                    new XElement(w + "r",
                        new XElement(w + "t", paraText.ToUpper())
                    )
                );

                //  Save the XML into the package
                using (XmlWriter xw =
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write)))
                {
                    xDoc.Save(xw);
                }

                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper());
            }
        }
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

    Public Function ParagraphText(ByVal e As XElement) As String
        Dim w As XNamespace = e.Name.Namespace
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))
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

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite)
            Dim docPackageRelationship As PackageRelationship = wdPackage _
                    .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", _
                            UriKind.Relative), docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                Dim xDoc As XDocument = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = documentPart _
                        .GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                Dim stylePart As PackagePart = Nothing
                Dim styleDoc As XDocument = Nothing

                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri( _
                            documentUri, styleRelation.TargetUri)
                    stylePart = wdPackage.GetPart(styleUri)

                    ' Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If

                Dim paraNode As XElement = xDoc.Root.<w:body>...<w:p>.FirstOrDefault()

                Dim paraText As String = ParagraphText(paraNode)

                ' Remove all text runs.
                paraNode...<w:r>.Remove()

                paraNode.Add(<w:r><w:t><%= paraText.ToUpper() %></w:t></w:r>)

                ' Save the XML into the package.
                Using xw As XmlWriter = _
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write))
                    xDoc.Save(xw)
                End Using

                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper())
            End If
        End Using
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<
```

`SampleDoc.docx`Bu programı çalıştırdıktan sonra açarsanız, bu programın belgedeki ilk paragrafı büyük harflere dönüştürdüğünü görebilirsiniz.

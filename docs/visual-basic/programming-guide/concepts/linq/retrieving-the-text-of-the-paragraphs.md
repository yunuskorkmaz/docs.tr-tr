---
title: (Visual Basic) paragrafların metnini alma
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 6d6f3e705e3a776f772a3507ef932d0715d2fb90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706621"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a>(Visual Basic) paragrafların metnini alma
Bu örnek önceki örneğe, yapılar [Their stilleri (Visual Basic) ve paragrafları alma](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). Bu yeni örnek, her bir paragraf metni bir dize olarak alır.  
  
 Bu örnek metni almak için anonim türlerin koleksiyonunu yinelenir ve yeni bir üye özelliğinin eklenmesiyle birlikte yeni bir koleksiyon anonim bir türün projeleri ek bir sorgu ekler `Text`. Kullandığı <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi bir dizede birleştirmek için standart sorgu işleci.  
  
 Bu teknik (diğer bir deyişle, ilk anonim bir türün bir koleksiyona yansıtma ve ardından bu anonim bir türün yeni bir koleksiyon için proje koleksiyonuna kullanarak), ortak ve kullanışlı bir deyim olur. Bu sorgu için ilk anonim tür yansıtma olmadan yazılmış. Ancak, geç değerlendirme nedeniyle Bunun yapılması bu nedenle kadar ek işlem gücü kullanmaz. Deyim, yığında daha kısa süreli nesneleri oluşturur, ancak bu önemli ölçüde performansı düşmez.  
  
 Elbette, paragraflar, her bir paragraf stilini ve her paragraf metnini almak için işlevini içeren tek bir sorgu yazmayı mümkün olacaktır. Ancak, genellikle birden çok sorgulara daha karmaşık bir sorgu sonuç kodunu daha modüler ve bakımı kolay olduğundan bölmeniz yararlı olur. Sorgu bölümünü yeniden gerekiyorsa, bu şekilde sorguları yazılır, ayrıca, bunu yeniden düzenlenmesi kolaydır.  
  
 Birbirine zincirlenmiş, bu sorguları konusunda ayrıntılı incelenen işlem model kullanmak [Öğreticisi: Ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, öğe düğümü, stil adı ve her bir paragraf metni belirleme WordprocessingML belgesinin işler. Bu örnek, önceki örneklerde üzerinde Bu öğreticide oluşturur. Yeni sorgu aşağıdaki kod açıklamalarda çağrılır.  
  
 Bu örneğin kaynak belge oluşturma yönergeleri için bkz. [kaynak Office Open XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Bu örnek WindowsBase derlemesinden sınıfları kullanır. Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because VB does not support short circuit evaluation  
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
  
 Bu örnek aşağıdaki belgede açıklanan uygulandığında çıktıyı üretir [kaynak Office Open XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
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
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki örnekte yerine bir uzantı yöntemini kullanmayı gösterir <xref:System.Linq.Enumerable.Aggregate%2A>, tek bir dize olarak birden çok dizeyi birleştirme.  
  
-   [Bir genişletme yöntemi (Visual Basic) kullanarak yeniden düzenleme](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Öğretici: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [Ertelenmiş yürütme ve geç değerlendirme LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

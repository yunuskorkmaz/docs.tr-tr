---
title: (Visual Basic) paragrafları metin alma
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: f1a7bc607fb51a8dca6121ee950af0252ab4722e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647156"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a>(Visual Basic) paragrafları metin alma
Bu örnek önceki örnekte olduğu derlemeler [Their stilleri (Visual Basic) ve paragrafları alma](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). Bu yeni örnek her paragraf metnini dize olarak alır.  
  
 Metni almak için bu örnek anonim türler toplulukta tekrarlanan ve yeni bir üye eklenmesi, yeni bir anonim bir tür koleksiyonunu projeleri ek bir sorgu, `Text`. Kullandığı <xref:System.Linq.Enumerable.Aggregate%2A> bir dizeye birden çok dizeyi birleştirme için standart sorgu işleci.  
  
 Bu teknik (diğer bir deyişle, ilk anonim bir türün bir koleksiyona yansıtma, sonra bu koleksiyona yeni bir koleksiyon anonim bir türün projeye kullanarak), ortak ve kullanışlı bir deyim olur. Bu sorgu için ilk anonim tür yansıtma olmadan yazılmış. Ancak, geç değerlendirme nedeniyle bunun nedenle kadar ek işleme gücünü kullanmaz. Deyim öbek üzerinde daha kısa süreli nesneleri oluşturur, ancak bu önemli ölçüde performans düşebilir değil.  
  
 Elbette, paragraflar, her paragraf stili ve her paragraf metni almak için kullanılan işlevler içeren tek bir sorgu yazmak mümkün olacaktır. Ancak, genellikle birden çok sorgu içine daha karmaşık bir sorgu sonuç kodu daha modüler ve sürdürmek daha kolay olduğundan bölmeniz yararlı olur. Sorgu bir kısmı kullanmanız gerekiyorsa, sorguları bu şekilde yazılır, ayrıca, bu düzenleme için kolaydır.  
  
 Konusunda ayrıntılı incelenir işleme model birlikte Zincirli olan, bu sorguları kullanmak [Öğreticisi: ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, öğe düğümü, stil adı ve her paragraf metnini belirleme WordprocessingML belgeye işler. Bu örnek önceki örnekler üzerinde Bu öğreticide oluşturur. Yeni sorgu aşağıdaki kodu açıklamalarda belirtilmiştir.  
  
 Bu örnek için kaynak belge oluşturma yönergeleri için bkz: [kaynak Office Açık XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Bu örnek WindowsBase derlemeden sınıfları kullanır. Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
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
  
 Bu örnek aşağıdaki açıklandığı belgeye uygulandığında çıktı üretir [kaynak Office Açık XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
 Sonraki örnek yerine bir genişletme yöntemi kullanmayı gösterir <xref:System.Linq.Enumerable.Aggregate%2A>, tek bir dize halinde birden çok dizeyi birleştirme için.  
  
-   [Bir genişletme yöntemi (Visual Basic) kullanarak yeniden düzenleme](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Düzenleme içeriği WordprocessingML belgesinde (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

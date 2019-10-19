---
title: Paragrafları ve stillerini alma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 4bc20556fb668db2db3e6bcfa42e96cc0d963b93
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582146"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Paragrafları ve stillerini alma (Visual Basic)
Bu örnekte, bir WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazdık. Ayrıca her bir paragrafın stilini belirler.  
  
 Bu sorgu, stil listesinden varsayılan stili alan [varsayılan paragraf stilini (Visual Basic) bularak](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), önceki örnekteki sorgu üzerinde oluşturulur. Bu bilgiler, sorgunun açıkça ayarlanmış bir stile sahip olmayan paragrafların stilini belirleyebilmesi için gereklidir. Paragraf stilleri `w:pPr` öğesi ile ayarlanır; bir paragraf bu öğeyi içermiyorsa, varsayılan stille biçimlendirilir.  
  
 Bu konuda, sorgunun bazı parçalarının önemi açıklanmakta ve sorgu tam, çalışan bir örnek kapsamında gösteriliyor.  
  
## <a name="example"></a>Örnek  
 Belgedeki tüm paragrafları ve bunların stillerini almak için sorgunun kaynağı aşağıdaki gibidir:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Bu ifade, önceki örnekteki sorgunun kaynağına benzer, [varsayılan paragraf stilini (Visual Basic) buluyor](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Temel fark, <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni yerine <xref:System.Xml.Linq.XContainer.Descendants%2A> eksenini kullanmadır. Sorgu, bölüm içeren belgelerde,, gövde öğesinin doğrudan alt öğeleri olmayacak şekilde <xref:System.Xml.Linq.XContainer.Descendants%2A> eksenini kullanır; Bunun yerine, paragraflar hiyerarşide iki düzey olur. @No__t_0 eksenini kullanarak, kod belgenin bölüm kullanıp kullanmadığını belirtir.  
  
## <a name="example"></a>Örnek  
 Sorgu, stil düğümünü içeren öğeyi belirlemede bir `Let` yan tümcesi kullanır. Öğe yoksa `styleNode` `Nothing` olarak ayarlanır:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 @No__t_0 yan tümcesi ilk olarak `pPr` adlı tüm öğeleri bulmak için <xref:System.Xml.Linq.XContainer.Elements%2A> eksenini kullanır, sonra `pStyle` adlı tüm alt öğeleri bulmak için <xref:System.Xml.Linq.Extensions.Elements%2A> genişletme yöntemini kullanır ve son olarak, koleksiyonu tek bir olarak dönüştürmek için <xref:System.Linq.Enumerable.FirstOrDefault%2A> standart sorgu işlecini kullanır. Koleksiyon boşsa, `styleNode` `Nothing` olarak ayarlanır. Bu, `pStyle` alt düğümünü aramak için kullanışlı bir deyimdir. @No__t_0 alt düğümü yoksa, bir özel durum oluşturarak kodun, veya başarısız olduğunu unutmayın; Bunun yerine, bu `Let` yan tümcesinin istenen davranışı olan `styleNode` `Nothing` olarak ayarlanır.  
  
 Sorgu, `StyleName` ve `ParagraphNode` iki üyeli anonim bir tür koleksiyonunu projeler.  
  
## <a name="example"></a>Örnek  
 Bu örnek, WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler. Ayrıca her bir paragrafın stilini belirler. Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır. Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.  
  
 Kaynak [Office Open XML belgesi (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)bölümünde bu örnek için kaynak belge oluşturma yönergelerini bulabilirsiniz.  
  
 Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır. @No__t_0 ad alanındaki türleri kullanır.  
  
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
  
 Bu örnek, [kaynak Office Open XML belgesi (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.  
  
```console  
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
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bir sonraki konu başlığında, [paragrafların metnini (Visual Basic) alırken](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), paragrafların metnini almak için bir sorgu oluşturacaksınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

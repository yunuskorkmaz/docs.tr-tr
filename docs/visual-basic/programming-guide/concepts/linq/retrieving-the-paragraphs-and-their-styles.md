---
title: Paragrafları ve bunların stilleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 5b8075b5aa05c32d2dc894149a8fa53f103138c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648313"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Paragrafları ve bunların stilleri (Visual Basic)
Bu örnekte, paragraf düğümleri WordprocessingML belgeden alır bir sorgu yazın. Ayrıca, her paragraf stilini tanımlar.  
  
 Bu sorgu önceki örnekte, sorgu inşa edilmiştir [varsayılan paragraf stili (Visual Basic) bulma](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), stilleri listesinden varsayılan stilini alır. Sorgu açıkça ayarlanmış bir stil yok paragrafları stilini bulabilmeniz bu bilgiler gereklidir. Paragraf stilleri aracılığıyla ayarlanır `w:pPr` öğesi; bir paragraf bu öğe içermiyorsa, varsayılan stiliyle biçimlendirilir.  
  
 Bu konuda sorgunun bazı parçalar önemini açıklar ve ardından sorguyu eksiksiz, çalışan bir örnek bir parçası olarak gösterir.  
  
## <a name="example"></a>Örnek  
 Bir belge ve bunların stiller tüm paragrafları almaya yönelik sorgu kaynağı aşağıdaki gibidir:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Bu ifade önceki örnekte, sorgunun kaynağını benzer [varsayılan paragraf stil (Visual Basic) bulma](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). İkisi arasındaki temel fark, kullanmasıdır <xref:System.Xml.Linq.XContainer.Descendants%2A> yerine eksen <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni. Sorgu kullanan <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen belgelerde, bölümler olduğundan paragrafları body öğesi doğrudan alt olmaz; bunun yerine, paragrafları iki düzey aşağı hiyerarşi içinde olacaktır. Kullanarak <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen, kod çalışır belge bölümleri desteklemediğini kullanır.  
  
## <a name="example"></a>Örnek  
 Sorgu kullanan bir `Let` stili düğümü içeren öğeyi belirlemek üzere yan tümcesi. Hiçbir öğe yoksa, ardından `styleNode` ayarlanır `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let` Yan tümcesi ilk kullanır <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksen `pPr`, sonra kullanır <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemi `pStyle`ve son olarak kullanan <xref:System.Linq.Enumerable.FirstOrDefault%2A> standart sorgu Koleksiyon bir tekliye dönüştürmek için işleci. Koleksiyon boş ise, `styleNode` ayarlanır `Nothing`. Aranacak yararlı bir deyim budur `pStyle` alt düğümü. Unutmayın `pPr` kod mu ya da bir özel durum; atma tarafından başarısız alt düğüm yok, bunun yerine, `styleNode` ayarlanır `Nothing`, bunun istediğiniz davranış olduğu `Let` yan tümcesi.  
  
 Anonim bir türün bir koleksiyon iki üyeleriyle sorgu projeleri `StyleName` ve `ParagraphNode`.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir WordprocessingML belgeden paragraf düğümleri alınıyor WordprocessingML belgeye işler. Ayrıca, her paragraf stilini tanımlar. Bu örnek önceki örnekler üzerinde Bu öğreticide oluşturur. Yeni sorgu aşağıdaki kodu açıklamalarda belirtilmiştir.  
  
 Bu örnekte, kaynak belge oluşturmak için yönergeler bulabilirsiniz [kaynak Office Açık XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Bu örnek WindowsBase derlemesinde sınıfları kullanır. Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
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
  
 Bu örnek aşağıdaki açıklandığı belgeye uygulandığında çıktı üretir [kaynak Office Açık XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
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
 Sonraki konusunda [(Visual Basic) paragrafları metin alma](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), paragraf metni almak için bir sorgu oluşturacaksınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Düzenleme içeriği WordprocessingML belgesinde (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

---
title: Paragrafları ve stillerini (Visual Basic) alma
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 3c6554c44c95db13aada0d9edf96cc2df595c6d1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816947"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Paragrafları ve stillerini (Visual Basic) alma
Bu örnekte biz WordprocessingML belgeden paragraf düğümleri alan bir sorgu yazın. Ayrıca, her bir paragraf stilini tanımlar.  
  
 Bu sorgu önceki örnekte, sorguda geliştirir [(Visual Basic) varsayılan paragraf stilini bulma](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), stilleri listesinden varsayılan stilini alır. Bu bilgiler, böylece sorgu açıkça ayarlanmış bir stil sahip değil paragraflar stilini gereklidir. Stilleri aracılığıyla ayarlanır `w:pPr` öğesi; bir paragraf bu öğe içermiyorsa varsayılan stili ile biçimlendirilir.  
  
 Bu konuda bazı parçalar sorgunun önemini açıklar ve ardından sorguyu eksiksiz, çalışan bir örnek bir parçası olarak gösterir.  
  
## <a name="example"></a>Örnek  
 Bir belge ve stillerini tüm paragraflarda almaya yönelik sorgu kaynağı aşağıdaki gibidir:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Bu ifade, önceki örnekte, sorgunun kaynak benzerdir [(Visual Basic) varsayılan paragraf stilini bulma](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). İkisi arasındaki temel fark, kullanmasıdır <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yerine <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni. Sorgu kullanan <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen paragrafları belgeleri, bölüm olduğundan gövde öğesinin doğrudan alt olmaz; bunun yerine, paragraf iki düzeyi aşağı hiyerarşide olacaktır. Kullanarak <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen, kod çalışır belgenin bölüm olup olmadığını kullanır.  
  
## <a name="example"></a>Örnek  
 Sorgu kullanan bir `Let` stil düğümü içeren öğe belirlemek için yan tümcesi. Hiçbir öğe yoksa, ardından `styleNode` ayarlanır `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let` Yan tümcesinin ilk kullanır <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksen `pPr`, ardından kullanır <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemi `pStyle`ve son olarak kullanan <xref:System.Linq.Enumerable.FirstOrDefault%2A> standart sorgu koleksiyon için bir singleton dönüştürmek için işleci. Koleksiyon boşsa, `styleNode` ayarlanır `Nothing`. Aramak için kullanışlı bir deyim budur `pStyle` alt düğümü. Unutmayın `pPr` alt düğüm mevcut değil, kod yok ya da; özel durum ile başarısız oluyor bunun yerine, `styleNode` ayarlanır `Nothing`, istenen davranışı olduğu `Let` yan tümcesi.  
  
 Anonim bir türün bir koleksiyon iki üyeli sorgu projeleri `StyleName` ve `ParagraphNode`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, paragraf düğümleri WordprocessingML belge alınırken WordprocessingML belgesinin işler. Ayrıca, her bir paragraf stilini tanımlar. Bu örnek, önceki örneklerde üzerinde Bu öğreticide oluşturur. Yeni sorgu aşağıdaki kod açıklamalarda çağrılır.  
  
 Bu örnekte için kaynak belge oluşturma için yönergeler bulabilirsiniz [kaynak Office Open XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Bu örnekte WindowsBase derlemede bulunan sınıfları kullanır. Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
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
  
 Bu örnek aşağıdaki belgede açıklanan uygulandığında çıktıyı üretir [kaynak Office Open XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
 Bir sonraki konu başlığında [(Visual Basic) paragrafların metnini alma](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), paragraf metnini almak için bir sorgu oluşturacaksınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

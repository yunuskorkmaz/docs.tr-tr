---
title: (Visual Basic) varsayılan paragraf stilini bulma
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 0694c9144e44e4a5de262f97581eb18943937243
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931319"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a>(Visual Basic) varsayılan paragraf stilini bulma
WordprocessingML belgesinin öğreticide düzenleme bilgileri ilk görevi, belgede varsayılan paragraf stilini bulmaktır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paket belge ve stil bölümlerini bulur ve ardından varsayılan stil adı bulan bir sorgu yürütür. Office Open XML belge paketler ve oluşmalıdır ve parçaları hakkında daha fazla bilgi için bkz. [ayrıntıları, Office Open XML WordprocessingML belgelerinin (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Sorgunun bulacağı adlı bir düğüm `w:style` adlı bir öznitelik olan `w:type` "paragraf" değerini ve ayrıca sahip bir öznitelik adlandırılmış `w:default` değerini "1" ile. Sorgu kullanır, bu öznitelikleri yalnızca bir XML düğümüyle olacaktır çünkü <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> için tek bir koleksiyon dönüştürme işleci. Ardından bir ada sahip bir öznitelik değerini alır `w:styleId`.  
  
 Bu örnek WindowsBase derlemesinden sınıfları kullanır. Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
### <a name="code"></a>Kod  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Açıklamalar  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki örnekte, bir belge ve stillerini paragraflar bulur benzer bir sorgu oluşturacaksınız:  
  
- [Paragrafları ve stillerini (Visual Basic) alma](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

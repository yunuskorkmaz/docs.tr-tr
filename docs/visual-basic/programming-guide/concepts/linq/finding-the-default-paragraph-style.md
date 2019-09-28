---
title: Varsayılan paragraf stilini bulma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 6754c48148e81b02eb8c63843b57bc3d28a5774a
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352891"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a>Varsayılan paragraf stilini bulma (Visual Basic)
WordprocessingML belgesi öğreticisindeki düzenleme bilgilerinde ilk görev, belgede varsayılan paragraf stilini bullevidir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paketin belge ve stil parçalarını bulur ve ardından varsayılan stil adını bulan bir sorgu yürütür. Office Open XML belge paketleri ve içerdikleri parçalar hakkında daha fazla bilgi için bkz. [Office Open XML WordprocessingML belgelerinin ayrıntıları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Sorgu, "paragraf" değerine sahip `w:type` adlı ve ayrıca "1" değerine sahip `w:default` adlı bir özniteliğe sahip `w:style` adlı bir düğüm bulur. Bu özniteliklere sahip yalnızca bir XML düğümü olacağı için, sorgu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> işlecini kullanarak bir koleksiyonu tek başına dönüştürür. Daha sonra `w:styleId` adlı özniteliğin değerini alır.  
  
 Bu örnek, WindowsBase derlemesinden sınıfları kullanır. @No__t-0 ad alanındaki türleri kullanır.  
  
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
  
```console  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki örnekte, bir belgedeki ve stillerinin tüm paragraflarını bulan benzer bir sorgu oluşturacaksınız:  
  
- [Paragrafları ve stillerini alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesinde Içerik işleme (Visual Basic) ](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

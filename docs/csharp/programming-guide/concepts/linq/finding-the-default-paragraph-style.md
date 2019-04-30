---
title: Varsayılan paragraf stilini (C#) bulma
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 052accf31007001c0fa0d46870ee6e4cd30f6bb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668230"
---
# <a name="finding-the-default-paragraph-style-c"></a>Varsayılan paragraf stilini (C#) bulma
WordprocessingML belgesinin öğreticide düzenleme bilgileri ilk görevi, belgede varsayılan paragraf stilini bulmaktır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paket belge ve stil bölümlerini bulur ve ardından varsayılan stil adı bulan bir sorgu yürütür. Office Open XML belge paketler ve oluşmalıdır ve parçaları hakkında daha fazla bilgi için bkz. [ayrıntıları, Office Open XML WordprocessingML belgelerinin (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Sorgunun bulacağı adlı bir düğüm `w:style` adlı bir öznitelik olan `w:type` "paragraf" değerini ve ayrıca sahip bir öznitelik adlandırılmış `w:default` değerini "1" ile. Sorgu kullanır, bu öznitelikleri yalnızca bir XML düğümüyle olacaktır çünkü <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> için tek bir koleksiyon dönüştürme işleci. Ardından bir ada sahip bir öznitelik değerini alır `w:styleId`.  
  
 Bu örnek WindowsBase derlemesinden sınıfları kullanır. Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
### <a name="code"></a>Kod  
  
```csharp  
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
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a>Açıklamalar  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki örnekte, bir belge ve stillerini paragraflar bulur benzer bir sorgu oluşturacaksınız:  
  
- [Paragrafları ve stillerini (C#) alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesindeki içeriği düzenleme](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

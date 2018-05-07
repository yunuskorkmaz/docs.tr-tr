---
title: Varsayılan paragraf stili (C#) bulma
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e29ca281e1867a72a76a28765912c39675ca0f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="finding-the-default-paragraph-style-c"></a>Varsayılan paragraf stili (C#) bulma
İlk WordprocessingML belge öğretici düzenleme bilgileri belgede paragrafları varsayılan stilini bulmak için bir görevdir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir Office Açık XML WordprocessingML belgesini açar, paket belge ve stil bölümlerini bulur ve varsayılan stil adı bulan bir sorgu yürütür. Office Açık XML belge paketleri ve bunların oluşur bölümleri hakkında daha fazla bilgi için bkz: [ayrıntıları, Office Açık XML WordprocessingML belgeleri (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Sorgu adlı bir düğüm bulana `w:style` adlı bir özniteliği olan `w:type` "paragraf" değerini ve ayrıca sahip bir öznitelik adlı `w:default` "1" değerine sahip. Bu öznitelikler ile yalnızca bir XML düğümü olacağından sorgusu kullanan <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> için tek bir koleksiyon dönüştürmek için işleci. Ardından adı olan özniteliğin değerini alır `w:styleId`.  
  
 Bu örnek WindowsBase derlemeden sınıfları kullanır. Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
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
 Bu örnek şu çıkışı üretir:  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki örnekte, bir belge ve bunların stiller tüm paragrafları bulur benzer bir sorgu oluşturursunuz:  
  
-   [Paragrafları ve bunların stilleri (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: WordprocessingML Belgesindeki İçeriği Düzenleme](http://msdn.microsoft.com/library/2696355e-4f83-4eaf-91b2-baa721f42fb4)

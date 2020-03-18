---
title: Varsayılan Paragraf Stilini Bulma (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 8cc1f1b9df208b0b180e5fe4a50922b5ee46b480
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169538"
---
# <a name="finding-the-default-paragraph-style-c"></a>Varsayılan Paragraf Stilini Bulma (C#)
WordprocessingML Belge öğreticisinde Bilgileri Manipüle Etme'deki ilk görev, belgedeki paragrafların varsayılan stilini bulmaktır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesini açar, belgeve stil bölümlerini bulur ve sonra varsayılan stil adını bulan bir sorgu yürütür. Office Open XML belge paketleri ve bunların oluşan bölümleri hakkında bilgi [için](./wordprocessingml-document-with-styles.md)Bkz.  
  
 Sorgu, "paragraf" `w:style` değeriyle adında `w:type` bir özniteliği olan ve "1" değeriyle `w:default` de adlandırılan bir özniteliği olan bir düğüm bulur. Bu özniteliklere sahip yalnızca bir XML düğümü olacağından, sorgu bir koleksiyonu singletona dönüştürmek için <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> işleci kullanır. Daha sonra özniteliğin değerini adı `w:styleId`ile alır.  
  
 Bu örnek, WindowsBase derlemesi sınıflarını kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.  
  
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
  
### <a name="comments"></a>Yorumlar  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki örnekte, belgedeki tüm paragrafları ve stillerini bulan benzer bir sorgu oluşturursunuz:  
  
- [Paragrafları ve Stillerinin Alınması (C#)](./retrieving-the-paragraphs-and-their-styles.md)  

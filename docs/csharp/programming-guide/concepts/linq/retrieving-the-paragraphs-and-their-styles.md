---
title: Paragrafları ve stillerini (C#) alma
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 46ffc13c9808b6186efa402bd46b75c6c1a9bbda
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510780"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Paragrafları ve stillerini (C#) alma
Bu örnekte biz WordprocessingML belgeden paragraf düğümleri alan bir sorgu yazın. Ayrıca, her bir paragraf stilini tanımlar.  
  
 Bu sorgu önceki örnekte, sorguda geliştirir [(C#) varsayılan paragraf stilini bulma](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), stilleri listesinden varsayılan stilini alır. Bu bilgiler, böylece sorgu açıkça ayarlanmış bir stil sahip değil paragraflar stilini gereklidir. Stilleri aracılığıyla ayarlanır `w:pPr` öğesi; bir paragraf bu öğe içermiyorsa varsayılan stili ile biçimlendirilir.  
  
 Bu konuda bazı parçalar sorgunun önemini açıklar ve ardından sorguyu eksiksiz, çalışan bir örnek bir parçası olarak gösterir.  
  
## <a name="example"></a>Örnek  
 Bir belge ve stillerini tüm paragraflarda almaya yönelik sorgu kaynağı aşağıdaki gibidir:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Bu ifade, önceki örnekte, sorgunun kaynak benzerdir [varsayılan paragraf stilini (C#) bulma](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). İkisi arasındaki temel fark, kullanmasıdır <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yerine <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni. Sorgu kullanan <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen paragrafları belgeleri, bölüm olduğundan gövde öğesinin doğrudan alt olmaz; bunun yerine, paragraf iki düzeyi aşağı hiyerarşide olacaktır. Kullanarak <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen, kod çalışır belgenin bölüm olup olmadığını kullanır.  
  
## <a name="example"></a>Örnek  
 Sorgu kullanan bir `let` stil düğümü içeren öğe belirlemek için yan tümcesi. Hiçbir öğe yoksa, ardından `styleNode` ayarlanır `null`:  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let` Yan tümcesinin ilk kullanır <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksen `pPr`, ardından kullanır <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemi `pStyle`ve son olarak kullanan <xref:System.Linq.Enumerable.FirstOrDefault%2A> standart sorgu koleksiyon için bir singleton dönüştürmek için işleci. Koleksiyon boşsa, `styleNode` ayarlanır `null`. Aramak için kullanışlı bir deyim budur `pStyle` alt düğümü. Unutmayın `pPr` alt düğüm mevcut değil, kod yok ya da; özel durum ile başarısız oluyor bunun yerine, `styleNode` ayarlanır `null`, istenen davranışı olduğu `let` yan tümcesi.  
  
 Anonim bir türün bir koleksiyon iki üyeli sorgu projeleri `StyleName` ve `ParagraphNode`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, paragraf düğümleri WordprocessingML belge alınırken WordprocessingML belgesinin işler. Ayrıca, her bir paragraf stilini tanımlar. Bu örnek, önceki örneklerde üzerinde Bu öğreticide oluşturur. Yeni sorgu aşağıdaki kod açıklamalarda çağrılır.  
  
 Bu örnekte için kaynak belge oluşturma için yönergeler bulabilirsiniz [kaynak Office Open XML belgesi (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Bu örnekte WindowsBase derlemede bulunan sınıfları kullanır. Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Following is the new query that finds all paragraphs in the  
// document and their styles.  
var paragraphs =  
    from para in xDoc  
                 .Root  
                 .Element(w + "body")  
                 .Descendants(w + "p")  
    let styleNode = para  
                    .Elements(w + "pPr")  
                    .Elements(w + "pStyle")  
                    .FirstOrDefault()  
    select new  
    {  
        ParagraphNode = para,  
        StyleName = styleNode != null ?  
            (string)styleNode.Attribute(w + "val") :  
            defaultStyle  
    };  
  
foreach (var p in paragraphs)  
    Console.WriteLine("StyleName:{0}", p.StyleName);  
```  
  
 Bu örnek aşağıdaki belgede açıklanan uygulandığında çıktıyı üretir [kaynak Office Open XML belgesi (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
 Bir sonraki konu başlığında [(C#) paragrafların metnini alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), paragraf metnini almak için bir sorgu oluşturacaksınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Öğretici: WordprocessingML belgesindeki (C#) içerik düzenleme](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

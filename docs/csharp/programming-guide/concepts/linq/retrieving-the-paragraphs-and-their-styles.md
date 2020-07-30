---
title: Paragrafları ve stillerini alma (C#)
description: Paragrafları alıp her paragrafın stilini tanımlayan bir sorgu yazmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 94d01a13485f70bc9d9cef55b5f390c3b30d7f14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303406"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Paragrafları ve stillerini alma (C#)
Bu örnekte, bir WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazdık. Ayrıca her bir paragrafın stilini belirler.  
  
 Bu sorgu, stil listesinden varsayılan stili alan [varsayılan paragraf stilini (C#) bularak](./finding-the-default-paragraph-style.md), önceki örnekteki sorgu üzerinde oluşturulur. Bu bilgiler, sorgunun açıkça ayarlanmış bir stile sahip olmayan paragrafların stilini belirleyebilmesi için gereklidir. Paragraf stilleri öğe aracılığıyla ayarlanır `w:pPr` ; bir paragraf bu öğeyi içermiyorsa, varsayılan stille biçimlendirilir.  
  
 Bu konuda, sorgunun bazı parçalarının önemi açıklanmakta ve sorgu tam, çalışan bir örnek kapsamında gösteriliyor.  
  
## <a name="example"></a>Örnek  
 Belgedeki tüm paragrafları ve bunların stillerini almak için sorgunun kaynağı aşağıdaki gibidir:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Bu ifade, önceki örnekteki sorgunun kaynağına benzer, [varsayılan paragraf stilini (C#) buluyor](./finding-the-default-paragraph-style.md). Temel fark, <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yerine eksenin kullanıldığı bir değer <xref:System.Xml.Linq.XContainer.Elements%2A> . Sorgu, bölümleri bulunan <xref:System.Xml.Linq.XContainer.Descendants%2A> belgelerde, paragrafları, gövde öğesinin doğrudan alt öğeleri olmayacak şekilde kullanır; bunun yerine, paragraflar hiyerarşide iki düzey olur. <xref:System.Xml.Linq.XContainer.Descendants%2A>Eksen kullanılarak, kod belgenin bölüm kullanıp kullanmadığını belirtir.  
  
## <a name="example"></a>Örnek  
 Sorgu, `let` Stil düğümünü içeren öğeyi belirlemede bir yan tümce kullanır. Öğe yoksa, şu `styleNode` şekilde ayarlanır `null` :  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let`Yan tümcesi ilk olarak <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksenini kullanır `pPr` , ardından <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemini kullanır `pStyle` ve son olarak, <xref:System.Linq.Enumerable.FirstOrDefault%2A> koleksiyonu tek bir tekil öğesine dönüştürmek için standart sorgu işlecini kullanır. Koleksiyon boşsa, `styleNode` olarak ayarlanır `null` . Bu, alt düğümü aramak için kullanışlı bir deyimdir `pStyle` . `pPr`Alt düğüm yoksa, bir özel durum oluşturarak kodun bir istisna olduğunu veya başarısız olduğunu, bunun yerine, `styleNode` `null` Bu yan tümcesinin istenen davranışı olan olarak ayarlandığını unutmayın `let` .  
  
 Sorgu, iki üyeli anonim bir türün bir koleksiyonunu `StyleName` ve `ParagraphNode` .  
  
## <a name="example"></a>Örnek  
 Bu örnek, WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler. Ayrıca her bir paragrafın stilini belirler. Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır. Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.  
  
 Kaynak [Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde bu örnek için kaynak belge oluşturma yönergelerini bulabilirsiniz.  
  
 Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.  
  
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
  
 Bu örnek, [kaynak Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.  
  
```output  
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
 Bir sonraki konu başlığında, [paragrafların metnini (C#) alırken](./retrieving-the-text-of-the-paragraphs.md), paragrafların metnini almak için bir sorgu oluşturacaksınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (C#)](./shape-of-wordprocessingml-documents.md)

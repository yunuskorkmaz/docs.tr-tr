---
title: Paragrafları ve Stillerinin Alınması (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 47127b6f1d6bfaa0d8d93333882a0d0b59f1bae6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168303"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Paragrafları ve Stillerinin Alınması (C#)
Bu örnekte, WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazarız. Ayrıca her paragrafın stilini tanımlar.  
  
 Bu sorgu, önceki örnekte varsayılan stil stilini stillistesinden alan [Varsayılan Paragraf Stilini (C#) bulma](./finding-the-default-paragraph-style.md)sorgusuüzerine oluşturur. Bu bilgiler, sorgunun açıkça ayarlanmış bir stili olmayan paragrafların stilini tanımlayabilmesi için gereklidir. Paragraf stilleri `w:pPr` öğe üzerinden ayarlanır; bir paragraf bu öğeyi içermiyorsa, varsayılan stil ile biçimlendirilir.  
  
 Bu konu, sorgunun bazı parçalarının önemini açıklar, ardından sorguyu tam, çalışan bir örneğin parçası olarak gösterir.  
  
## <a name="example"></a>Örnek  
 Belgedeki tüm paragrafları ve stilleri almak için sorgunun kaynağı aşağıdaki gibidir:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Bu ifade, önceki örnekte, Varsayılan Paragraf [Stilini Bulma (C#)](./finding-the-default-paragraph-style.md)sorgusunun kaynağına benzer. Temel fark, eksen yerine <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni <xref:System.Xml.Linq.XContainer.Elements%2A> kullanmasıdır. Sorgu ekseni <xref:System.Xml.Linq.XContainer.Descendants%2A> kullanır, çünkü bölümleri olan belgelerde paragraflar gövde öğesinin doğrudan alt öğesi olmayacaktır; bunun yerine, paragraflar hiyerarşide iki düzey aşağı olacaktır. Kodun <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni kullanarak, belgenin bölümleri kullanıp kullanmadığı üzerinde çalışacağız.  
  
## <a name="example"></a>Örnek  
 Sorgu, stil `let` düğümü içeren öğeyi belirlemek için bir yan tümce kullanır. Eleman yoksa, `styleNode` şu şekilde `null`ayarlanır:  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 Yan `let` tümce <xref:System.Xml.Linq.XContainer.Elements%2A> önce adlı `pPr`tüm öğeleri bulmak <xref:System.Xml.Linq.Extensions.Elements%2A> için ekseni kullanır, `pStyle`sonra adlandırılmış <xref:System.Linq.Enumerable.FirstOrDefault%2A> tüm alt öğeleri bulmak için uzantı yöntemini kullanır ve son olarak koleksiyonu bir singleton'a dönüştürmek için standart sorgu işleci kullanır. Koleksiyon boşsa, `styleNode` '' `null`olarak ayarlanır. `pStyle` Bu, soyundan gelen düğümü aramak için yararlı bir deyimdir. `pPr` Alt düğüm yoksa, kod bir özel durum atarak başarısız ne de yok unutmayın; bunun `styleNode` yerine, `null`bu `let` maddenin istenilen davranışı , olarak ayarlanır.  
  
 Sorgu, iki üyeden `StyleName` oluşan anonim bir `ParagraphNode`türde bir koleksiyon ve .  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler. Ayrıca her paragrafın stilini tanımlar. Bu örnek, bu öğreticide önceki örneklere dayanmaktadır. Yeni sorgu aşağıdaki koddaki açıklamalarda çağrılır.  
  
 [Kaynak Office Açık XML Belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bu örnek için kaynak belge oluşturmak için yönergeleri bulabilirsiniz.  
  
 Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.  
  
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
  
 Bu örnek, [Kaynak Office Açık XML Belgesi (C#) oluşturma'da](./creating-the-source-office-open-xml-document.md)açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.  
  
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
 Bir sonraki konu, [Paragrafmetni (C#) alma,](./retrieving-the-text-of-the-paragraphs.md)paragrafmetni almak için bir sorgu oluşturursunuz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)](./shape-of-wordprocessingml-documents.md)

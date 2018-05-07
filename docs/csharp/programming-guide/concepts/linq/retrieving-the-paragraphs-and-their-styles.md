---
title: Paragrafları ve bunların stilleri (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 11788c1fa46c63c78a9db0255c8e84250285863e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Paragrafları ve bunların stilleri (C#)
Bu örnekte, paragraf düğümleri WordprocessingML belgeden alır bir sorgu yazın. Ayrıca, her paragraf stilini tanımlar.  
  
 Bu sorgu önceki örnekte, sorgu inşa edilmiştir [varsayılan paragraf stili (C#) bulma](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), stilleri listesinden varsayılan stilini alır. Sorgu açıkça ayarlanmış bir stil yok paragrafları stilini bulabilmeniz bu bilgiler gereklidir. Paragraf stilleri aracılığıyla ayarlanır `w:pPr` öğesi; bir paragraf bu öğe içermiyorsa, varsayılan stiliyle biçimlendirilir.  
  
 Bu konuda sorgunun bazı parçalar önemini açıklar ve ardından sorguyu eksiksiz, çalışan bir örnek bir parçası olarak gösterir.  
  
## <a name="example"></a>Örnek  
 Bir belge ve bunların stiller tüm paragrafları almaya yönelik sorgu kaynağı aşağıdaki gibidir:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Bu ifade önceki örnekte, sorgunun kaynağını benzer [varsayılan paragraf stil (C#) bulma](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). İkisi arasındaki temel fark, kullanmasıdır <xref:System.Xml.Linq.XContainer.Descendants%2A> yerine eksen <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni. Sorgu kullanan <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen belgelerde, bölümler olduğundan paragrafları body öğesi doğrudan alt olmaz; bunun yerine, paragrafları iki düzey aşağı hiyerarşi içinde olacaktır. Kullanarak <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen, kod çalışır belge bölümleri desteklemediğini kullanır.  
  
## <a name="example"></a>Örnek  
 Sorgu kullanan bir `let` stili düğümü içeren öğeyi belirlemek üzere yan tümcesi. Hiçbir öğe yoksa, ardından `styleNode` ayarlanır `null`:  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let` Yan tümcesi ilk kullanır <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksen `pPr`, sonra kullanır <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemi `pStyle`ve son olarak kullanan <xref:System.Linq.Enumerable.FirstOrDefault%2A> standart sorgu Koleksiyon bir tekliye dönüştürmek için işleci. Koleksiyon boş ise, `styleNode` ayarlanır `null`. Aranacak yararlı bir deyim budur `pStyle` alt düğümü. Unutmayın `pPr` kod mu ya da bir özel durum; atma tarafından başarısız alt düğüm yok, bunun yerine, `styleNode` ayarlanır `null`, bunun istediğiniz davranış olduğu `let` yan tümcesi.  
  
 Anonim bir türün bir koleksiyon iki üyeleriyle sorgu projeleri `StyleName` ve `ParagraphNode`.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir WordprocessingML belgeden paragraf düğümleri alınıyor WordprocessingML belgeye işler. Ayrıca, her paragraf stilini tanımlar. Bu örnek önceki örnekler üzerinde Bu öğreticide oluşturur. Yeni sorgu aşağıdaki kodu açıklamalarda belirtilmiştir.  
  
 Bu örnekte, kaynak belge oluşturmak için yönergeler bulabilirsiniz [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Bu örnek WindowsBase derlemesinde sınıfları kullanır. Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
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
  
 Bu örnek aşağıdaki açıklandığı belgeye uygulandığında çıktı üretir [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
 Sonraki konusunda [(C#) paragrafları metin alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), paragraf metni almak için bir sorgu oluşturacaksınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

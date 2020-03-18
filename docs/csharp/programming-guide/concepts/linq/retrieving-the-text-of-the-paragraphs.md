---
title: Paragrafmetninin Alınması (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 7c47420045def3fe973169e01143646c0f60a8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168251"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Paragrafmetninin Alınması (C#)
Bu örnek, önceki örnekte, [Paragrafları ve Stilleri (C#) alma](./retrieving-the-paragraphs-and-their-styles.md)üzerine oluşturur. Bu yeni örnek, her paragrafın metnini bir dize olarak alır.  
  
 Metni almak için, bu örnek, anonim türlerin toplanması yoluyla yineleyen ek bir sorgu ekler ve yeni bir üye `Text`nin eklenmesiyle anonim bir türden oluşan yeni bir koleksiyon projeleri, . Birden çok <xref:System.Linq.Enumerable.Aggregate%2A> dizeyi tek bir dize ye dönüştürmek için standart sorgu işleci kullanır.  
  
 Bu teknik (yani, ilk anonim bir tür bir koleksiyona yansıtma, daha sonra anonim bir tür yeni bir koleksiyona proje için bu koleksiyonu kullanarak) yaygın ve yararlı bir deyimdir. Bu sorgu, ilk anonim türe yansıtılmadan yazılmış olabilir. Ancak, tembel değerlendirme nedeniyle, bunu yapmak çok ek işlem gücü kullanmaz. Deyim yığın üzerinde daha kısa ömürlü nesneler oluşturur, ancak bu önemli ölçüde performansı düşürmez.  
  
 Elbette, paragrafları, her paragrafın stilini ve her paragrafın metnini almak için işlevselliği içeren tek bir sorgu yazmak mümkündür. Ancak, ortaya çıkan kod daha modüler ve bakımı daha kolay olduğundan, daha karmaşık bir sorguyu birden çok sorguya ayırmak genellikle yararlıdır. Ayrıca, sorgunun bir bölümünü yeniden kullanmanız gerekiyorsa, sorgular bu şekilde yazılmışsa yeniden düzenlemeyapmak daha kolaydır.  
  
 Birlikte zincirlenmiş olan bu sorgular, konu Öğretici ayrıntılı olarak incelenir işleme modeli kullanın: Birlikte [Sorguları Zincirleme (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, öğe düğümü, stil adı ve her paragrafın metnini belirleyerek bir WordprocessingML belgesini işler. Bu örnek, bu öğreticide önceki örneklere dayanmaktadır. Yeni sorgu aşağıdaki koddaki açıklamalarda çağrılır.  
  
 Bu örnek için kaynak belge oluşturma yönergeleri için [bkz.](./creating-the-source-office-open-xml-document.md)  
  
 Bu örnek, WindowsBase derlemesi sınıflarını kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.  
  
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
  
string defaultStyle =
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Find all paragraphs in the document.  
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
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 Bu örnek, [Kaynak Office Açık XML Belgesi (C#) oluşturma'da](./creating-the-source-office-open-xml-document.md)açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.  
  
```output  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki örnek, birden çok dizeyi <xref:System.Linq.Enumerable.Aggregate%2A>tek bir dize içine dönüştürmek yerine bir uzantı yönteminin nasıl kullanılacağını gösterir.  
  
- [Uzantı Yöntemini Kullanarak Yeniden Düzenleme (C#)](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)](shape-of-wordprocessingml-documents.md)
- [Linq'te Ertelenmiş Yürütme ve Tembel Değerlendirme XML 'ye (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

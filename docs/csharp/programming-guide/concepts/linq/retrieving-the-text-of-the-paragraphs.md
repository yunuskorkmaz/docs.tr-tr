---
title: Paragrafları (C#) metin alma
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 07a289ec8c3f0c783a9c85cb1d25d17164008e06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Paragrafları (C#) metin alma
Bu örnek önceki örnekte olduğu derlemeler [Their stilleri (C#) ve paragrafları alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). Bu yeni örnek her paragraf metnini dize olarak alır.  
  
 Metni almak için bu örnek anonim türler toplulukta tekrarlanan ve yeni bir üye eklenmesi, yeni bir anonim bir tür koleksiyonunu projeleri ek bir sorgu, `Text`. Kullandığı <xref:System.Linq.Enumerable.Aggregate%2A> bir dizeye birden çok dizeyi birleştirme için standart sorgu işleci.  
  
 Bu teknik (diğer bir deyişle, ilk anonim bir türün bir koleksiyona yansıtma, sonra bu koleksiyona yeni bir koleksiyon anonim bir türün projeye kullanarak), ortak ve kullanışlı bir deyim olur. Bu sorgu için ilk anonim tür yansıtma olmadan yazılmış. Ancak, geç değerlendirme nedeniyle bunun nedenle kadar ek işleme gücünü kullanmaz. Deyim öbek üzerinde daha kısa süreli nesneleri oluşturur, ancak bu önemli ölçüde performans düşebilir değil.  
  
 Elbette, paragraflar, her paragraf stili ve her paragraf metni almak için kullanılan işlevler içeren tek bir sorgu yazmak mümkün olacaktır. Ancak, genellikle birden çok sorgu içine daha karmaşık bir sorgu sonuç kodu daha modüler ve sürdürmek daha kolay olduğundan bölmeniz yararlı olur. Sorgu bir kısmı kullanmanız gerekiyorsa, sorguları bu şekilde yazılır, ayrıca, bu düzenleme için kolaydır.  
  
 Konusunda ayrıntılı incelenir işleme model birlikte Zincirli olan, bu sorguları kullanmak [Öğreticisi: zincirleme sorguları birlikte (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, öğe düğümü, stil adı ve her paragraf metnini belirleme WordprocessingML belgeye işler. Bu örnek önceki örnekler üzerinde Bu öğreticide oluşturur. Yeni sorgu aşağıdaki kodu açıklamalarda belirtilmiştir.  
  
 Bu örnek için kaynak belge oluşturma yönergeleri için bkz: [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Bu örnek WindowsBase derlemeden sınıfları kullanır. Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
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
  
 Bu örnek aşağıdaki açıklandığı belgeye uygulandığında çıktı üretir [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
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
 Sonraki örnek yerine bir genişletme yöntemi kullanmayı gösterir <xref:System.Linq.Enumerable.Aggregate%2A>, tek bir dize halinde birden çok dizeyi birleştirme için.  
  
-   [Bir genişletme yöntemi (C#) kullanarak yeniden düzenleme](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

---
title: Saf Bir Fonksiyon Kullanarak Yeniden Düzenleme (C#)
ms.date: 07/20/2015
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
ms.openlocfilehash: f264a0028ed265a5a4fbe1dc32f430c648724c20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253085"
---
# <a name="refactoring-using-a-pure-function-c"></a><span data-ttu-id="1f8a6-102">Saf Bir Fonksiyon Kullanarak Yeniden Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="1f8a6-102">Refactoring Using a Pure Function (C#)</span></span>
<span data-ttu-id="1f8a6-103">Aşağıdaki örnek, önceki örnekte, [Bir Uzantı Yöntemini Kullanarak Yeniden Düzenleme (C#)](./refactoring-using-an-extension-method.md), bu örnekte saf bir işlev kullanmak için, paragraf metnini bulmak için kod saf statik yönteme `ParagraphText`taşınır.</span><span class="sxs-lookup"><span data-stu-id="1f8a6-103">The following example refactors the previous example, [Refactoring Using an Extension Method (C#)](./refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f8a6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f8a6-104">Example</span></span>  
 <span data-ttu-id="1f8a6-105">Bu örnek, bir WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="1f8a6-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="1f8a6-106">Ayrıca her paragrafın stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1f8a6-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="1f8a6-107">Bu örnek, bu öğreticide önceki örneklere dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f8a6-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="1f8a6-108">Refactored kodu aşağıdaki kodda yorum denir.</span><span class="sxs-lookup"><span data-stu-id="1f8a6-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="1f8a6-109">Bu örnek için kaynak belge oluşturma yönergeleri için [bkz.](./creating-the-source-office-open-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="1f8a6-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="1f8a6-110">Bu örnek, WindowsBase derlemesi sınıflarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f8a6-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="1f8a6-111"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f8a6-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    // This is a new method that assembles the paragraph text.  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
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
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri,  
                      styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
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
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="1f8a6-112">Bu örnek, yeniden düzenlemeden önceki yle aynı çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1f8a6-112">This example produces the same output as before the refactoring:</span></span>  
  
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
  
### <a name="next-steps"></a><span data-ttu-id="1f8a6-113">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="1f8a6-113">Next Steps</span></span>  
 <span data-ttu-id="1f8a6-114">Sonraki örnek, XML'nin nasıl farklı bir şekle yansıtılabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="1f8a6-114">The next example shows how to project XML into a different shape:</span></span>  
  
- [<span data-ttu-id="1f8a6-115">XML'i Farklı Bir Şekilde Yansıtma (C#)</span><span class="sxs-lookup"><span data-stu-id="1f8a6-115">Projecting XML in a Different Shape (C#)</span></span>](./projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f8a6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f8a6-116">See also</span></span>

- [<span data-ttu-id="1f8a6-117">Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)</span><span class="sxs-lookup"><span data-stu-id="1f8a6-117">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="1f8a6-118">Uzantı Yöntemini Kullanarak Yeniden Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="1f8a6-118">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)
- [<span data-ttu-id="1f8a6-119">Saf Fonksiyonlara Yeniden Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="1f8a6-119">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)

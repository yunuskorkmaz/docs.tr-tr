---
title: (C#) Word belgelerinde metin bulma
ms.date: 07/20/2015
ms.assetid: 82f86677-560b-49dc-a089-610409939b2a
ms.openlocfilehash: 9f81795c00c29da34bb5f229afb557eb89af6509
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487500"
---
# <a name="finding-text-in-word-documents-c"></a><span data-ttu-id="edd6c-102">(C#) Word belgelerinde metin bulma</span><span class="sxs-lookup"><span data-stu-id="edd6c-102">Finding Text in Word Documents (C#)</span></span>
<span data-ttu-id="edd6c-103">Bu konu faydalı bir şey için önceki sorguları genişletir: bir dizenin tüm örnekleri belgede bulun.</span><span class="sxs-lookup"><span data-stu-id="edd6c-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edd6c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="edd6c-104">Example</span></span>  
 <span data-ttu-id="edd6c-105">Bu örnek, belgede belirli bir metin parçası tüm oluşumlarını bulmak için bir WordprocessingML belgesinin işler.</span><span class="sxs-lookup"><span data-stu-id="edd6c-105">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="edd6c-106">Bunu yapmak için "Hello" dizesi bulan bir sorgu kullanırız.</span><span class="sxs-lookup"><span data-stu-id="edd6c-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="edd6c-107">Bu örnek, önceki örneklerde üzerinde Bu öğreticide oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edd6c-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="edd6c-108">Yeni sorgu aşağıdaki kod açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="edd6c-108">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="edd6c-109">Bu örneğin kaynak belge oluşturma yönergeleri için bkz. [kaynak Office Open XML belgesi (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="edd6c-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="edd6c-110">Bu örnekte WindowsBase derlemede bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="edd6c-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="edd6c-111">Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="edd6c-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
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
  
        // Following is the new query that retrieves all paragraphs  
        // that have specific text in them.  
        var helloParagraphs =  
            from para in paraWithText  
            where para.Text.Contains("Hello")  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in helloParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="edd6c-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="edd6c-112">This example produces the following output:</span></span>  
  
```  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="edd6c-113">Elbette, böylece belirli bir stil satırıyla arar arama değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edd6c-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="edd6c-114">Aşağıdaki sorgu, kod stili sahip tüm boş satırları bulur:</span><span class="sxs-lookup"><span data-stu-id="edd6c-114">The following query finds all blank lines that have the Code style:</span></span>  
  
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
  
        // Retrieve all paragraphs that have no text and are styled Code.  
        var blankCodeParagraphs =  
            from para in paraWithText  
            where para.Text == "" && para.StyleName == "Code"  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in blankCodeParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="edd6c-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="edd6c-115">This example produces the following output:</span></span>  
  
```  
StyleName:Code ><  
```  
  
 <span data-ttu-id="edd6c-116">Elbette, bu örnek, çeşitli yollarla iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="edd6c-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="edd6c-117">Örneğin, metni aramak için normal ifadeler kullanabiliriz, size belirli bir dizin ve benzeri tüm Word dosyaları yinelemek.</span><span class="sxs-lookup"><span data-stu-id="edd6c-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="edd6c-118">Tek bir sorgu yazılmışlar gibi bu örnek yaklaşık de unutmayın.</span><span class="sxs-lookup"><span data-stu-id="edd6c-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="edd6c-119">Her sorgu yavaş, ertelenmiş bir şekilde uygulandığından, sorgu yinelendiğinde kadar her sorgu sonuçlarını vermez.</span><span class="sxs-lookup"><span data-stu-id="edd6c-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="edd6c-120">Yürütme ve geç değerlendirme hakkında daha fazla bilgi için bkz. [ertelenmiş yürütme ve geç değerlendirme LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="edd6c-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="edd6c-121">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="edd6c-121">Next Steps</span></span>  
 <span data-ttu-id="edd6c-122">Sonraki bölümde WordprocessingML belgelerinin hakkında daha fazla bilgi verilmektedir:</span><span class="sxs-lookup"><span data-stu-id="edd6c-122">The next section provides more information about WordprocessingML documents:</span></span>  
  
- [<span data-ttu-id="edd6c-123">Ayrıntılar Office Open XML WordprocessingML belgelerinin (C#)</span><span class="sxs-lookup"><span data-stu-id="edd6c-123">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/wordprocessingml-document-with-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="edd6c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edd6c-124">See also</span></span>

- [<span data-ttu-id="edd6c-125">Öğretici: WordprocessingML belgesindeki içeriği düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="edd6c-125">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="edd6c-126">Saf işlev (C#) kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="edd6c-126">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)
- [<span data-ttu-id="edd6c-127">Ertelenmiş yürütme ve geç değerlendirme LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="edd6c-127">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

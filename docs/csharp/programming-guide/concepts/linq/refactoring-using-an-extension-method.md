---
title: Bir genişletme yöntemi (C#) kullanarak yeniden düzenleme
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: 0f41c4b4357125b6c92b17d8c818a0cfcf9822e7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596190"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="2890e-102">Bir genişletme yöntemi (C#) kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="2890e-102">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="2890e-103">Bu örnek önceki örneğe, yapılar [(C#) paragrafların metnini alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), yeniden düzenleme bir genişletme yöntemi uygulanan saf işlev kullanarak dizeleri birleşimi tarafından.</span><span class="sxs-lookup"><span data-stu-id="2890e-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="2890e-104">Önceki örnekte kullanılan <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi bir dizede birleştirmek için standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="2890e-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="2890e-105">Ancak, elde edilen sorgu daha küçük ve daha basit olduğundan, bunu yapmak için bir uzantı metodu yazma daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="2890e-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2890e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2890e-106">Example</span></span>  
 <span data-ttu-id="2890e-107">Bu örnekte paragraflar, her paragraf stilini ve her bir paragraf metni alınırken WordprocessingML belgesinin işler.</span><span class="sxs-lookup"><span data-stu-id="2890e-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="2890e-108">Bu örnek, önceki örneklerde üzerinde Bu öğreticide oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2890e-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="2890e-109">Örnek, birden çok aşırı yükleme içerir `StringConcatenate` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2890e-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="2890e-110">Bu örnekte için kaynak belge oluşturma için yönergeler bulabilirsiniz [kaynak Office Open XML belgesi (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="2890e-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="2890e-111">Bu örnek WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2890e-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="2890e-112">Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2890e-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
```  
  
## <a name="example"></a><span data-ttu-id="2890e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2890e-113">Example</span></span>  
 <span data-ttu-id="2890e-114">Dört aşırı yükleme `StringConcatenate` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2890e-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="2890e-115">Aşırı yüklemelerden birine yalnızca dizeleri koleksiyonunu alır ve tek bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="2890e-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="2890e-116">Başka bir aşırı herhangi bir tür ve temsilci koleksiyonu bu projelerden koleksiyonun tek bir dize alabilir.</span><span class="sxs-lookup"><span data-stu-id="2890e-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="2890e-117">Bir ayırıcı dizesinde belirtmenize olanak veren iki daha fazla aşırı yüklemesi vardır.</span><span class="sxs-lookup"><span data-stu-id="2890e-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="2890e-118">Aşağıdaki kod, tüm dört aşırı yüklemeler kullanır.</span><span class="sxs-lookup"><span data-stu-id="2890e-118">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="2890e-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2890e-119">This example produces the following output:</span></span>  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="2890e-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="2890e-120">Example</span></span>  
 <span data-ttu-id="2890e-121">Şimdi, örneğin yeni bir genişletme yöntemi yararlanmak için değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="2890e-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
                Text = para  
                       .ParagraphNode  
                       .Elements(w + "r")  
                       .Elements(w + "t")  
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="2890e-122">Bu örnek aşağıdaki belgede açıklanan uygulandığında çıktıyı üretir [kaynak Office Open XML belgesi (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="2890e-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="2890e-123">Bu yeniden düzenleme, yeniden düzenleme saf işlev bir değişken olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2890e-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="2890e-124">Bir sonraki konu başlığında, daha ayrıntılı saf işlevler halinde hesaba katacak şekilde fikri başlatacaktır.</span><span class="sxs-lookup"><span data-stu-id="2890e-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2890e-125">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="2890e-125">Next Steps</span></span>  
 <span data-ttu-id="2890e-126">Sonraki örnek, saf işlevler kullanarak başka bir yolla bu kodu yeniden düzenleyin gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2890e-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="2890e-127">(Visual Basic) saf işlev kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="2890e-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="2890e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2890e-128">See also</span></span>

- [<span data-ttu-id="2890e-129">Öğretici: WordprocessingML belgesindeki içeriği düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="2890e-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="2890e-130">Saf işlevler halinde (C#) yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="2890e-130">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

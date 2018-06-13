---
title: Bir genişletme yöntemi (C#) kullanarak yeniden düzenleme
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: f3a1d64aebc04d772209dbe867e6d729de087127
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335490"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="c1752-102">Bir genişletme yöntemi (C#) kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="c1752-102">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="c1752-103">Bu örnek önceki örnekte olduğu derlemeler [(C#) paragrafları metin alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), bir genişletme yöntemi uygulanan saf işlevi kullanarak dizeleri birleşimini yeniden düzenleme tarafından.</span><span class="sxs-lookup"><span data-stu-id="c1752-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="c1752-104">Önceki örnekte kullanılan <xref:System.Linq.Enumerable.Aggregate%2A> bir dizeye birden çok dizeyi birleştirme için standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="c1752-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="c1752-105">Ancak, elde edilen sorgu olduğundan daha küçük ve daha basit Bunu yapmak için uzantı metodu yazma daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="c1752-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1752-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1752-106">Example</span></span>  
 <span data-ttu-id="c1752-107">Bu örnek alma paragraflar, her paragraf stili ve her paragraf metni WordprocessingML belgeye işler.</span><span class="sxs-lookup"><span data-stu-id="c1752-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="c1752-108">Bu örnek önceki örnekler üzerinde Bu öğreticide oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1752-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="c1752-109">Örnek, birden çok aşırı içerir `StringConcatenate` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c1752-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="c1752-110">Bu örnekte, kaynak belge oluşturmak için yönergeler bulabilirsiniz [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c1752-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="c1752-111">Bu örnek WindowsBase derlemeden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1752-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="c1752-112">Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c1752-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c1752-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1752-113">Example</span></span>  
 <span data-ttu-id="c1752-114">Dört aşırı `StringConcatenate` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c1752-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="c1752-115">Aşırı yüklemesiyle yalnızca dizeleri koleksiyonu alır ve tek bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1752-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="c1752-116">Başka bir aşırı herhangi bir türü ve temsilci koleksiyonunu o koleksiyonun bir singleton projelerinden dizeye alabilir.</span><span class="sxs-lookup"><span data-stu-id="c1752-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="c1752-117">Ayırıcı dize belirlemenizi sağlayan iki daha fazla aşırı vardır.</span><span class="sxs-lookup"><span data-stu-id="c1752-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="c1752-118">Aşağıdaki kod tüm dört aşırı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1752-118">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="c1752-119">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c1752-119">This example produces the following output:</span></span>  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="c1752-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1752-120">Example</span></span>  
 <span data-ttu-id="c1752-121">Şimdi, örneğin, yeni uzantı metodu yararlanmak için değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="c1752-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
  
 <span data-ttu-id="c1752-122">Bu örnek aşağıdaki açıklandığı belgeye uygulandığında çıktı üretir [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c1752-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="c1752-123">Bu yeniden düzenleme saf bir işlevdeki yeniden düzenleme, bir değişken olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c1752-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="c1752-124">Sonraki konusunda daha ayrıntılı saf işlevler halinde Finansman fikir tanıtılacaktır.</span><span class="sxs-lookup"><span data-stu-id="c1752-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c1752-125">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="c1752-125">Next Steps</span></span>  
 <span data-ttu-id="c1752-126">Sonraki örnekte, bu kod, saf işlevlerini kullanarak başka bir yolla yeniden düzenlemeniz gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c1752-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
-   [<span data-ttu-id="c1752-127">Saf işlevi (Visual Basic) kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="c1752-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1752-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1752-128">See Also</span></span>  
 [<span data-ttu-id="c1752-129">Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)</span><span class="sxs-lookup"><span data-stu-id="c1752-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="c1752-130">Saf işlevlerini (C#) yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="c1752-130">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

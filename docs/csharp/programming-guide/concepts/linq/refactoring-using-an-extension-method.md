---
title: Uzantı Yöntemini Kullanarak Yeniden Düzenleme (C#)
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: 8546c2cb834107cf2e099af40f9a7df4d5858b4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253094"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="abcb8-102">Uzantı Yöntemini Kullanarak Yeniden Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="abcb8-102">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="abcb8-103">Bu örnek, bir uzantı yöntemi olarak uygulanan saf bir işlev kullanarak dizeleri concatenation refactoring tarafından, önceki örnek, [Paragraflar (C# ) Metni Alma](./retrieving-the-text-of-the-paragraphs.md)oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abcb8-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="abcb8-104">Önceki örnekte, <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi tek bir dize ye dönüştürmek için standart sorgu işleci kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="abcb8-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="abcb8-105">Ancak, ortaya çıkan sorgu daha küçük ve daha basit, çünkü bunu yapmak için bir uzantı yöntemi yazmak için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="abcb8-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abcb8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="abcb8-106">Example</span></span>  
 <span data-ttu-id="abcb8-107">Bu örnek, paragrafları, her paragrafın stilini ve her paragrafın metnini alan bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="abcb8-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="abcb8-108">Bu örnek, bu öğreticide önceki örneklere dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="abcb8-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="abcb8-109">Örnek, yöntemin birden `StringConcatenate` çok aşırı yüklemesini içerir.</span><span class="sxs-lookup"><span data-stu-id="abcb8-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="abcb8-110">[Kaynak Office Açık XML Belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bu örnek için kaynak belge oluşturmak için yönergeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abcb8-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="abcb8-111">Bu örnek, WindowsBase derlemesi sınıflarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="abcb8-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="abcb8-112"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="abcb8-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="abcb8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="abcb8-113">Example</span></span>  
 <span data-ttu-id="abcb8-114">`StringConcatenate` Yöntemin dört aşırı yükleri vardır.</span><span class="sxs-lookup"><span data-stu-id="abcb8-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="abcb8-115">Bir aşırı yükleme sadece dizeleri bir koleksiyon alır ve tek bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="abcb8-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="abcb8-116">Başka bir aşırı yükleme herhangi bir türde bir koleksiyon alabilir ve koleksiyonun singleton bir dize için projeler bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="abcb8-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="abcb8-117">Ayırıcı dize belirtmenize olanak tanıyan iki fazla yükleme daha vardır.</span><span class="sxs-lookup"><span data-stu-id="abcb8-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="abcb8-118">Aşağıdaki kod, dört aşırı yüklemeyi de kullanır.</span><span class="sxs-lookup"><span data-stu-id="abcb8-118">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="abcb8-119">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="abcb8-119">This example produces the following output:</span></span>  
  
```output  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="abcb8-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="abcb8-120">Example</span></span>  
 <span data-ttu-id="abcb8-121">Şimdi, örnek yeni uzantı yöntemiyararlanmak için değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="abcb8-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
  
 <span data-ttu-id="abcb8-122">Bu örnek, [Kaynak Office Açık XML Belgesi (C#) oluşturma'da](./creating-the-source-office-open-xml-document.md)açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="abcb8-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="abcb8-123">Bu yeniden düzenlemenin saf bir işleve yeniden düzenlemenin bir varyantı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="abcb8-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="abcb8-124">Bir sonraki konu daha ayrıntılı olarak saf işlevler içine faktoring fikrini tanıtacaktır.</span><span class="sxs-lookup"><span data-stu-id="abcb8-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="abcb8-125">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="abcb8-125">Next Steps</span></span>  
 <span data-ttu-id="abcb8-126">Sonraki örnek, saf işlevleri kullanarak bu kodu niçin başka bir şekilde yeniden düzenlediğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="abcb8-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="abcb8-127">Saf Bir İşlev Kullanarak Yeniden Düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abcb8-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="abcb8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abcb8-128">See also</span></span>

- [<span data-ttu-id="abcb8-129">Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)</span><span class="sxs-lookup"><span data-stu-id="abcb8-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="abcb8-130">Saf Fonksiyonlara Yeniden Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="abcb8-130">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)

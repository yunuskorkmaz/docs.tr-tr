---
title: Genişletme yöntemi kullanarak yeniden düzenleme (C#)
description: Bir genişletme yöntemi kullanarak kodu yeniden düzenleme hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: e786f0e1514156535fd6a6033e37ed8879e99709
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381950"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="0117b-104">Genişletme yöntemi kullanarak yeniden düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="0117b-104">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="0117b-105">Bu örnek, bir genişletme yöntemi olarak uygulanan bir saf işlev kullanarak dizelerin birleştirilmesiyle yeniden düzenleyerek, önceki örnekte yer alan, [paragrafların (C#) metnini alma](./retrieving-the-text-of-the-paragraphs.md).</span><span class="sxs-lookup"><span data-stu-id="0117b-105">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="0117b-106">Önceki örnek, <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi tek bir dizede birleştirmek için standart sorgu işlecini kullandı.</span><span class="sxs-lookup"><span data-stu-id="0117b-106">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="0117b-107">Bununla birlikte, bunu yapmak için bir genişletme yöntemi yazmak daha uygundur, çünkü sonuçta elde edilen sorgu daha küçük ve daha basit.</span><span class="sxs-lookup"><span data-stu-id="0117b-107">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0117b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0117b-108">Example</span></span>  
 <span data-ttu-id="0117b-109">Bu örnekte, bir WordprocessingML belgesi, paragrafları, her bir paragrafın stili ve her bir paragrafın metni işlenir.</span><span class="sxs-lookup"><span data-stu-id="0117b-109">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="0117b-110">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="0117b-110">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="0117b-111">Örnek, yönteminin birden çok aşırı yüklerini içerir `StringConcatenate` .</span><span class="sxs-lookup"><span data-stu-id="0117b-111">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="0117b-112">Kaynak [Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde bu örnek için kaynak belge oluşturma yönergelerini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0117b-112">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="0117b-113">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="0117b-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="0117b-114"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0117b-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0117b-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0117b-115">Example</span></span>  
 <span data-ttu-id="0117b-116">Metodun dört aşırı yüklemesi vardır `StringConcatenate` .</span><span class="sxs-lookup"><span data-stu-id="0117b-116">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="0117b-117">Bir aşırı yükleme yalnızca bir dize koleksiyonu alır ve tek bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="0117b-117">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="0117b-118">Başka bir aşırı yükleme, herhangi bir türün bir koleksiyonunu ve bir koleksiyonun tek bir sınıfından bir dizeye olan bir temsilciyi alabilir.</span><span class="sxs-lookup"><span data-stu-id="0117b-118">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="0117b-119">Bir ayırıcı dize belirtmenizi sağlayan iki aşırı yükleme daha vardır.</span><span class="sxs-lookup"><span data-stu-id="0117b-119">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="0117b-120">Aşağıdaki kod dört aşırı yüklemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0117b-120">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="0117b-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0117b-121">This example produces the following output:</span></span>  
  
```output  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="0117b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="0117b-122">Example</span></span>  
 <span data-ttu-id="0117b-123">Şimdi, örnek yeni uzantı yönteminden faydalanmak için değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="0117b-123">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
  
 <span data-ttu-id="0117b-124">Bu örnek, [kaynak Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="0117b-124">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="0117b-125">Bu yeniden düzenleme, saf bir işleve yeniden düzenleme çeşidine sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0117b-125">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="0117b-126">Sonraki konu, düzenleme işlevlerini saf işlevlere daha ayrıntılı bir şekilde tanıtacaktır.</span><span class="sxs-lookup"><span data-stu-id="0117b-126">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0117b-127">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="0117b-127">Next Steps</span></span>  
 <span data-ttu-id="0117b-128">Sonraki örnekte, saf işlevleri kullanılarak bu kodun başka bir şekilde nasıl yeniden düzenlenmesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0117b-128">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="0117b-129">Saf Işlev kullanarak yeniden düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="0117b-129">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
  
## <a name="see-also"></a><span data-ttu-id="0117b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0117b-130">See also</span></span>

- [<span data-ttu-id="0117b-131">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="0117b-131">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="0117b-132">Saf IŞLEVLERE yeniden düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="0117b-132">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)

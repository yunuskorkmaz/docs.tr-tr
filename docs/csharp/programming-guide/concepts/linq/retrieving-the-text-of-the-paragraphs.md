---
title: (C#) paragrafların metnini alma
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 1d23addb4c4c1ea17343585392fbe08fef08568a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180763"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="01c44-102">(C#) paragrafların metnini alma</span><span class="sxs-lookup"><span data-stu-id="01c44-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="01c44-103">Bu örnek önceki örneğe, yapılar [Their stilleri (C#) ve paragrafları alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="01c44-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="01c44-104">Bu yeni örnek, her bir paragraf metni bir dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="01c44-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="01c44-105">Bu örnek metni almak için anonim türlerin koleksiyonunu yinelenir ve yeni bir üye özelliğinin eklenmesiyle birlikte yeni bir koleksiyon anonim bir türün projeleri ek bir sorgu ekler `Text`.</span><span class="sxs-lookup"><span data-stu-id="01c44-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="01c44-106">Kullandığı <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi bir dizede birleştirmek için standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="01c44-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="01c44-107">Bu teknik (diğer bir deyişle, ilk anonim bir türün bir koleksiyona yansıtma ve ardından bu anonim bir türün yeni bir koleksiyon için proje koleksiyonuna kullanarak), ortak ve kullanışlı bir deyim olur.</span><span class="sxs-lookup"><span data-stu-id="01c44-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="01c44-108">Bu sorgu için ilk anonim tür yansıtma olmadan yazılmış.</span><span class="sxs-lookup"><span data-stu-id="01c44-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="01c44-109">Ancak, geç değerlendirme nedeniyle Bunun yapılması bu nedenle kadar ek işlem gücü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="01c44-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="01c44-110">Deyim, yığında daha kısa süreli nesneleri oluşturur, ancak bu önemli ölçüde performansı düşmez.</span><span class="sxs-lookup"><span data-stu-id="01c44-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="01c44-111">Elbette, paragraflar, her bir paragraf stilini ve her paragraf metnini almak için işlevini içeren tek bir sorgu yazmayı mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="01c44-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="01c44-112">Ancak, genellikle birden çok sorgulara daha karmaşık bir sorgu sonuç kodunu daha modüler ve bakımı kolay olduğundan bölmeniz yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="01c44-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="01c44-113">Sorgu bölümünü yeniden gerekiyorsa, bu şekilde sorguları yazılır, ayrıca, bunu yeniden düzenlenmesi kolaydır.</span><span class="sxs-lookup"><span data-stu-id="01c44-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="01c44-114">Birbirine zincirlenmiş, bu sorguları konusunda ayrıntılı incelenen işlem model kullanmak [Öğreticisi: zincirleme sorguları birlikte (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="01c44-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01c44-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="01c44-115">Example</span></span>  
 <span data-ttu-id="01c44-116">Bu örnekte, öğe düğümü, stil adı ve her bir paragraf metni belirleme WordprocessingML belgesinin işler.</span><span class="sxs-lookup"><span data-stu-id="01c44-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="01c44-117">Bu örnek, önceki örneklerde üzerinde Bu öğreticide oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01c44-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="01c44-118">Yeni sorgu aşağıdaki kod açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="01c44-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="01c44-119">Bu örneğin kaynak belge oluşturma yönergeleri için bkz. [kaynak Office Open XML belgesi (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="01c44-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="01c44-120">Bu örnek WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="01c44-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="01c44-121">Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="01c44-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="01c44-122">Bu örnek aşağıdaki belgede açıklanan uygulandığında çıktıyı üretir [kaynak Office Open XML belgesi (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="01c44-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="01c44-123">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="01c44-123">Next Steps</span></span>  
 <span data-ttu-id="01c44-124">Sonraki örnekte yerine bir uzantı yöntemini kullanmayı gösterir <xref:System.Linq.Enumerable.Aggregate%2A>, tek bir dize olarak birden çok dizeyi birleştirme.</span><span class="sxs-lookup"><span data-stu-id="01c44-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
-   [<span data-ttu-id="01c44-125">Bir genişletme yöntemi (C#) kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="01c44-125">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="01c44-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01c44-126">See Also</span></span>

- [<span data-ttu-id="01c44-127">Öğretici: WordprocessingML belgesindeki (C#) içerik düzenleme</span><span class="sxs-lookup"><span data-stu-id="01c44-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
- [<span data-ttu-id="01c44-128">Ertelenmiş yürütme ve geç değerlendirme LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="01c44-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

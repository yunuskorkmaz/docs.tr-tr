---
title: Paragrafları (C#) metin alma
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 07a289ec8c3f0c783a9c85cb1d25d17164008e06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327164"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="2b898-102">Paragrafları (C#) metin alma</span><span class="sxs-lookup"><span data-stu-id="2b898-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="2b898-103">Bu örnek önceki örnekte olduğu derlemeler [Their stilleri (C#) ve paragrafları alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="2b898-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="2b898-104">Bu yeni örnek her paragraf metnini dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2b898-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="2b898-105">Metni almak için bu örnek anonim türler toplulukta tekrarlanan ve yeni bir üye eklenmesi, yeni bir anonim bir tür koleksiyonunu projeleri ek bir sorgu, `Text`.</span><span class="sxs-lookup"><span data-stu-id="2b898-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="2b898-106">Kullandığı <xref:System.Linq.Enumerable.Aggregate%2A> bir dizeye birden çok dizeyi birleştirme için standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="2b898-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="2b898-107">Bu teknik (diğer bir deyişle, ilk anonim bir türün bir koleksiyona yansıtma, sonra bu koleksiyona yeni bir koleksiyon anonim bir türün projeye kullanarak), ortak ve kullanışlı bir deyim olur.</span><span class="sxs-lookup"><span data-stu-id="2b898-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="2b898-108">Bu sorgu için ilk anonim tür yansıtma olmadan yazılmış.</span><span class="sxs-lookup"><span data-stu-id="2b898-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="2b898-109">Ancak, geç değerlendirme nedeniyle bunun nedenle kadar ek işleme gücünü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="2b898-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="2b898-110">Deyim öbek üzerinde daha kısa süreli nesneleri oluşturur, ancak bu önemli ölçüde performans düşebilir değil.</span><span class="sxs-lookup"><span data-stu-id="2b898-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="2b898-111">Elbette, paragraflar, her paragraf stili ve her paragraf metni almak için kullanılan işlevler içeren tek bir sorgu yazmak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2b898-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="2b898-112">Ancak, genellikle birden çok sorgu içine daha karmaşık bir sorgu sonuç kodu daha modüler ve sürdürmek daha kolay olduğundan bölmeniz yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="2b898-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="2b898-113">Sorgu bir kısmı kullanmanız gerekiyorsa, sorguları bu şekilde yazılır, ayrıca, bu düzenleme için kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2b898-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="2b898-114">Konusunda ayrıntılı incelenir işleme model birlikte Zincirli olan, bu sorguları kullanmak [Öğreticisi: zincirleme sorguları birlikte (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="2b898-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b898-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b898-115">Example</span></span>  
 <span data-ttu-id="2b898-116">Bu örnek, öğe düğümü, stil adı ve her paragraf metnini belirleme WordprocessingML belgeye işler.</span><span class="sxs-lookup"><span data-stu-id="2b898-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="2b898-117">Bu örnek önceki örnekler üzerinde Bu öğreticide oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b898-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="2b898-118">Yeni sorgu aşağıdaki kodu açıklamalarda belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b898-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="2b898-119">Bu örnek için kaynak belge oluşturma yönergeleri için bkz: [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="2b898-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="2b898-120">Bu örnek WindowsBase derlemeden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b898-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="2b898-121">Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2b898-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="2b898-122">Bu örnek aşağıdaki açıklandığı belgeye uygulandığında çıktı üretir [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="2b898-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="2b898-123">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="2b898-123">Next Steps</span></span>  
 <span data-ttu-id="2b898-124">Sonraki örnek yerine bir genişletme yöntemi kullanmayı gösterir <xref:System.Linq.Enumerable.Aggregate%2A>, tek bir dize halinde birden çok dizeyi birleştirme için.</span><span class="sxs-lookup"><span data-stu-id="2b898-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
-   [<span data-ttu-id="2b898-125">Bir genişletme yöntemi (C#) kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="2b898-125">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b898-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b898-126">See Also</span></span>  
 [<span data-ttu-id="2b898-127">Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)</span><span class="sxs-lookup"><span data-stu-id="2b898-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="2b898-128">Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2b898-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

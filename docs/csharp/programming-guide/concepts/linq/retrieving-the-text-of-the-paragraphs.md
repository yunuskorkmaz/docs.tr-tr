---
title: Paragrafların metnini alma (C#)
description: Bir WordprocessingML belgesindeki her bir paragrafın metnini C# dilinde bir dize olarak almak için LINQ sorgularını nasıl kullanacağınızı öğrenin. Bu örnek, zincirleme sorguları kullanır.
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 58a07ab848307c886927815e4e49e90806f61346
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302600"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="6c214-104">Paragrafların metnini alma (C#)</span><span class="sxs-lookup"><span data-stu-id="6c214-104">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="6c214-105">Bu örnek, önceki örnekte yer alan [ve paragrafları ve stillerini alma (C#) ile](./retrieving-the-paragraphs-and-their-styles.md)oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c214-105">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="6c214-106">Bu yeni örnek, her bir paragrafın metnini dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6c214-106">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="6c214-107">Bu örnek, metni almak için anonim türler koleksiyonu ve proje, yeni bir üyenin eklenmesiyle anonim bir türün yeni bir koleksiyonu aracılığıyla yinelenen ek bir sorgu ekler `Text` .</span><span class="sxs-lookup"><span data-stu-id="6c214-107">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="6c214-108"><xref:System.Linq.Enumerable.Aggregate%2A>Birden çok dizeyi tek bir dizede birleştirmek için standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c214-108">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="6c214-109">Bu teknik (yani, ilk olarak anonim bir türün koleksiyonuna yansıtırken, daha sonra bu koleksiyonun yeni bir anonim tür koleksiyonuna proje için kullanılması) ortak ve kullanışlı bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="6c214-109">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="6c214-110">Bu sorgu, ilk anonim türe yansıtılamadan yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c214-110">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="6c214-111">Ancak, yavaş değerlendirme nedeniyle bunu yapmak çok daha fazla işlem gücü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="6c214-111">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="6c214-112">Deyim yığında daha kısa süreli nesneler oluşturur, ancak bu durum performansı önemli ölçüde düşürür.</span><span class="sxs-lookup"><span data-stu-id="6c214-112">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="6c214-113">Tabii ki, paragrafları alma işlevini, her bir paragrafın stilini ve her bir paragrafın metnini içeren tek bir sorgu yazmak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6c214-113">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="6c214-114">Ancak, sonuçta elde edilen kod daha modüler ve bakımını daha kolay olduğundan, genellikle daha karmaşık bir sorguyu birden çok sorguya bölmek faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="6c214-114">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="6c214-115">Ayrıca, sorgunun bir bölümünü yeniden kullanmanız gerekiyorsa, sorgular bu şekilde yazılmışsa yeniden düzenleme daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="6c214-115">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="6c214-116">Birlikte zincirleme olan bu sorgular, konu öğreticisinde ayrıntılı olarak incelenen işleme modelini kullanın [: sorguları birlikte zincirleme (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6c214-116">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c214-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c214-117">Example</span></span>  
 <span data-ttu-id="6c214-118">Bu örnekte, bir WordprocessingML belgesi işlenir, öğe düğümü, stil adı ve her paragrafın metni belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6c214-118">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="6c214-119">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="6c214-119">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="6c214-120">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6c214-120">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="6c214-121">Bu örnek için kaynak belge oluşturmaya ilişkin yönergeler için bkz. [kaynak Office Open XML belgesi oluşturma (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="6c214-121">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="6c214-122">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c214-122">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="6c214-123"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c214-123">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="6c214-124">Bu örnek, [kaynak Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="6c214-124">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="6c214-125">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="6c214-125">Next Steps</span></span>  
 <span data-ttu-id="6c214-126">Sonraki örnek, <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi tek bir dizeye birleştirmek için yerine bir genişletme yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c214-126">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="6c214-127">Genişletme yöntemi kullanarak yeniden düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="6c214-127">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="6c214-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c214-128">See also</span></span>

- [<span data-ttu-id="6c214-129">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="6c214-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="6c214-130">LINQ to XML ertelenmiş yürütme ve geç değerlendirme (C#)</span><span class="sxs-lookup"><span data-stu-id="6c214-130">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

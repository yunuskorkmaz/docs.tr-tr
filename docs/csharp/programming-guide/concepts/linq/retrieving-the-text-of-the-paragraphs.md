---
title: Paragrafların (C#) metnini alma
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 88a7e82a7d27048ce3f901e6e9d50b8737797adb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591081"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="c00f7-102">Paragrafların (C#) metnini alma</span><span class="sxs-lookup"><span data-stu-id="c00f7-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="c00f7-103">Bu örnek, önceki örnekte yer alan [ve paragrafları ve stilleriniC#() alma](./retrieving-the-paragraphs-and-their-styles.md)hakkında daha fazla örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c00f7-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="c00f7-104">Bu yeni örnek, her bir paragrafın metnini dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="c00f7-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="c00f7-105">Bu örnek, metni almak için anonim türler koleksiyonu ve proje, `Text`yeni bir üyenin eklenmesiyle anonim bir türün yeni bir koleksiyonu aracılığıyla yinelenen ek bir sorgu ekler.</span><span class="sxs-lookup"><span data-stu-id="c00f7-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="c00f7-106">Birden çok dizeyi <xref:System.Linq.Enumerable.Aggregate%2A> tek bir dizede birleştirmek için standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c00f7-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="c00f7-107">Bu teknik (yani, ilk olarak anonim bir türün koleksiyonuna yansıtırken, daha sonra bu koleksiyonun yeni bir anonim tür koleksiyonuna proje için kullanılması) ortak ve kullanışlı bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="c00f7-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="c00f7-108">Bu sorgu, ilk anonim türe yansıtılamadan yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="c00f7-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="c00f7-109">Ancak, yavaş değerlendirme nedeniyle bunu yapmak çok daha fazla işlem gücü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="c00f7-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="c00f7-110">Deyim yığında daha kısa süreli nesneler oluşturur, ancak bu durum performansı önemli ölçüde düşürür.</span><span class="sxs-lookup"><span data-stu-id="c00f7-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="c00f7-111">Tabii ki, paragrafları alma işlevini, her bir paragrafın stilini ve her bir paragrafın metnini içeren tek bir sorgu yazmak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c00f7-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="c00f7-112">Ancak, sonuçta elde edilen kod daha modüler ve bakımını daha kolay olduğundan, genellikle daha karmaşık bir sorguyu birden çok sorguya bölmek faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="c00f7-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="c00f7-113">Ayrıca, sorgunun bir bölümünü yeniden kullanmanız gerekiyorsa, sorgular bu şekilde yazılmışsa yeniden düzenleme daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="c00f7-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="c00f7-114">Birlikte zincirleme olan bu sorgular, konu [öğreticisinde ayrıntılı olarak incelenen işleme modelini kullanır: Sorguları birlikte (C#)](./tutorial-chaining-queries-together.md)zincirleme.</span><span class="sxs-lookup"><span data-stu-id="c00f7-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](./tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c00f7-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c00f7-115">Example</span></span>  
 <span data-ttu-id="c00f7-116">Bu örnekte, bir WordprocessingML belgesi işlenir, öğe düğümü, stil adı ve her paragrafın metni belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c00f7-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="c00f7-117">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="c00f7-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="c00f7-118">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c00f7-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="c00f7-119">Bu örnek için kaynak belge oluşturmaya ilişkin yönergeler için bkz. [kaynak Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c00f7-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="c00f7-120">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c00f7-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="c00f7-121"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c00f7-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="c00f7-122">Bu örnek, [kaynak Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="c00f7-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="c00f7-123">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="c00f7-123">Next Steps</span></span>  
 <span data-ttu-id="c00f7-124">Sonraki örnek, birden çok dizeyi tek bir dizeye birleştirmek için yerine <xref:System.Linq.Enumerable.Aggregate%2A>bir genişletme yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c00f7-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="c00f7-125">Bir genişletme yöntemi (C#) kullanılarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="c00f7-125">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="c00f7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c00f7-126">See also</span></span>

- [<span data-ttu-id="c00f7-127">Öğretici: WordprocessingML belgesinde (C#) içeriği düzenleme</span><span class="sxs-lookup"><span data-stu-id="c00f7-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="c00f7-128">LINQ to XML (C#) Içinde ertelenmiş yürütme ve geç değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c00f7-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

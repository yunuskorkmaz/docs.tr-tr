---
title: Paragrafları ve stillerini alma (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 4accbf3325ad4db95c028249c7071cb9fedd19cd
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591200"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="d36f8-102">Paragrafları ve stillerini alma (C#)</span><span class="sxs-lookup"><span data-stu-id="d36f8-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="d36f8-103">Bu örnekte, bir WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazdık.</span><span class="sxs-lookup"><span data-stu-id="d36f8-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="d36f8-104">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="d36f8-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="d36f8-105">Bu sorgu, stil listesinden varsayılan stili alan [varsayılan paragraf stilini (C#) bularak](./finding-the-default-paragraph-style.md), önceki örnekteki sorgu üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d36f8-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="d36f8-106">Bu bilgiler, sorgunun açıkça ayarlanmış bir stile sahip olmayan paragrafların stilini belirleyebilmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d36f8-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="d36f8-107">Paragraf stilleri `w:pPr` öğe aracılığıyla ayarlanır; bir paragraf bu öğeyi içermiyorsa, varsayılan stille biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d36f8-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="d36f8-108">Bu konuda, sorgunun bazı parçalarının önemi açıklanmakta ve sorgu tam, çalışan bir örnek kapsamında gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="d36f8-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d36f8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d36f8-109">Example</span></span>  
 <span data-ttu-id="d36f8-110">Belgedeki tüm paragrafları ve bunların stillerini almak için sorgunun kaynağı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d36f8-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="d36f8-111">Bu ifade, önceki örnekteki sorgunun kaynağına benzer, [varsayılan paragraf stilini (C#) buluyor](./finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="d36f8-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="d36f8-112">Temel fark, <xref:System.Xml.Linq.XContainer.Descendants%2A> <xref:System.Xml.Linq.XContainer.Elements%2A> eksen yerine eksenin kullanıldığı bir değer.</span><span class="sxs-lookup"><span data-stu-id="d36f8-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="d36f8-113">Sorgu, bölümleri bulunan <xref:System.Xml.Linq.XContainer.Descendants%2A> belgelerde, paragrafları, gövde öğesinin doğrudan alt öğeleri olmayacak şekilde kullanır; bunun yerine, paragraflar hiyerarşide iki düzey olur.</span><span class="sxs-lookup"><span data-stu-id="d36f8-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="d36f8-114"><xref:System.Xml.Linq.XContainer.Descendants%2A> Eksen kullanılarak, kod belgenin bölüm kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d36f8-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d36f8-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d36f8-115">Example</span></span>  
 <span data-ttu-id="d36f8-116">Sorgu, stil düğümünü `let` içeren öğeyi belirlemede bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="d36f8-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="d36f8-117">Öğe yoksa, `styleNode` şu şekilde `null`ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="d36f8-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="d36f8-118">`pPr` `pStyle` <xref:System.Linq.Enumerable.FirstOrDefault%2A> Yantümcesi<xref:System.Xml.Linq.Extensions.Elements%2A> ilk olarak adlı <xref:System.Xml.Linq.XContainer.Elements%2A> tüm öğeleri bulmak için eksenini kullanır, ardından adlı tüm alt öğeleri bulmak için genişletme yöntemini kullanır ve son olarak standart sorguyu kullanır `let` koleksiyonu bir tekil öğesine dönüştürecek işleç.</span><span class="sxs-lookup"><span data-stu-id="d36f8-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="d36f8-119">Koleksiyon boşsa, `styleNode` olarak `null`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d36f8-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="d36f8-120">Bu, alt düğümü aramak `pStyle` için kullanışlı bir deyimdir.</span><span class="sxs-lookup"><span data-stu-id="d36f8-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="d36f8-121">`pPr` Alt düğüm yoksa, bir özel durum oluşturarak kodun bir istisna olduğunu veya başarısız olduğunu, `styleNode` bunun yerine, bu `let` yan tümcesinin istenen davranışı olan `null`olarak ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d36f8-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="d36f8-122">Sorgu, `StyleName` iki üyeli anonim bir türün bir koleksiyonunu ve `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="d36f8-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d36f8-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="d36f8-123">Example</span></span>  
 <span data-ttu-id="d36f8-124">Bu örnek, WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="d36f8-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="d36f8-125">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="d36f8-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="d36f8-126">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="d36f8-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="d36f8-127">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d36f8-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="d36f8-128">Kaynak [Office Open XML belgesiC#() oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde bu örnek için kaynak belge oluşturma yönergelerini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d36f8-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="d36f8-129">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d36f8-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="d36f8-130"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d36f8-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
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
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Following is the new query that finds all paragraphs in the  
// document and their styles.  
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
  
foreach (var p in paragraphs)  
    Console.WriteLine("StyleName:{0}", p.StyleName);  
```  
  
 <span data-ttu-id="d36f8-131">Bu örnek, [kaynak Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="d36f8-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="d36f8-132">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="d36f8-132">Next Steps</span></span>  
 <span data-ttu-id="d36f8-133">Bir sonraki konu başlığında, [paragrafların (C#) metnini alırken](./retrieving-the-text-of-the-paragraphs.md), paragrafların metnini almak için bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d36f8-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d36f8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d36f8-134">See also</span></span>

- [<span data-ttu-id="d36f8-135">Öğretici: WordprocessingML belgesinde (C#) içeriği düzenleme</span><span class="sxs-lookup"><span data-stu-id="d36f8-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)

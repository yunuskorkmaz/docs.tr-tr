---
title: Paragrafları ve stillerini alma (C#)
description: Paragrafları alıp her paragrafın stilini tanımlayan bir sorgu yazmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 94d01a13485f70bc9d9cef55b5f390c3b30d7f14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303406"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="7668f-103">Paragrafları ve stillerini alma (C#)</span><span class="sxs-lookup"><span data-stu-id="7668f-103">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="7668f-104">Bu örnekte, bir WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazdık.</span><span class="sxs-lookup"><span data-stu-id="7668f-104">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="7668f-105">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="7668f-105">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="7668f-106">Bu sorgu, stil listesinden varsayılan stili alan [varsayılan paragraf stilini (C#) bularak](./finding-the-default-paragraph-style.md), önceki örnekteki sorgu üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7668f-106">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="7668f-107">Bu bilgiler, sorgunun açıkça ayarlanmış bir stile sahip olmayan paragrafların stilini belirleyebilmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7668f-107">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="7668f-108">Paragraf stilleri öğe aracılığıyla ayarlanır `w:pPr` ; bir paragraf bu öğeyi içermiyorsa, varsayılan stille biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7668f-108">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="7668f-109">Bu konuda, sorgunun bazı parçalarının önemi açıklanmakta ve sorgu tam, çalışan bir örnek kapsamında gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="7668f-109">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7668f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7668f-110">Example</span></span>  
 <span data-ttu-id="7668f-111">Belgedeki tüm paragrafları ve bunların stillerini almak için sorgunun kaynağı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7668f-111">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="7668f-112">Bu ifade, önceki örnekteki sorgunun kaynağına benzer, [varsayılan paragraf stilini (C#) buluyor](./finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="7668f-112">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="7668f-113">Temel fark, <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yerine eksenin kullanıldığı bir değer <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="7668f-113">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="7668f-114">Sorgu, bölümleri bulunan <xref:System.Xml.Linq.XContainer.Descendants%2A> belgelerde, paragrafları, gövde öğesinin doğrudan alt öğeleri olmayacak şekilde kullanır; bunun yerine, paragraflar hiyerarşide iki düzey olur.</span><span class="sxs-lookup"><span data-stu-id="7668f-114">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="7668f-115"><xref:System.Xml.Linq.XContainer.Descendants%2A>Eksen kullanılarak, kod belgenin bölüm kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7668f-115">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7668f-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="7668f-116">Example</span></span>  
 <span data-ttu-id="7668f-117">Sorgu, `let` Stil düğümünü içeren öğeyi belirlemede bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="7668f-117">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="7668f-118">Öğe yoksa, şu `styleNode` şekilde ayarlanır `null` :</span><span class="sxs-lookup"><span data-stu-id="7668f-118">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="7668f-119">`let`Yan tümcesi ilk olarak <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksenini kullanır `pPr` , ardından <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemini kullanır `pStyle` ve son olarak, <xref:System.Linq.Enumerable.FirstOrDefault%2A> koleksiyonu tek bir tekil öğesine dönüştürmek için standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7668f-119">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="7668f-120">Koleksiyon boşsa, `styleNode` olarak ayarlanır `null` .</span><span class="sxs-lookup"><span data-stu-id="7668f-120">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="7668f-121">Bu, alt düğümü aramak için kullanışlı bir deyimdir `pStyle` .</span><span class="sxs-lookup"><span data-stu-id="7668f-121">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="7668f-122">`pPr`Alt düğüm yoksa, bir özel durum oluşturarak kodun bir istisna olduğunu veya başarısız olduğunu, bunun yerine, `styleNode` `null` Bu yan tümcesinin istenen davranışı olan olarak ayarlandığını unutmayın `let` .</span><span class="sxs-lookup"><span data-stu-id="7668f-122">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="7668f-123">Sorgu, iki üyeli anonim bir türün bir koleksiyonunu `StyleName` ve `ParagraphNode` .</span><span class="sxs-lookup"><span data-stu-id="7668f-123">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7668f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="7668f-124">Example</span></span>  
 <span data-ttu-id="7668f-125">Bu örnek, WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="7668f-125">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="7668f-126">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="7668f-126">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="7668f-127">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="7668f-127">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="7668f-128">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7668f-128">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="7668f-129">Kaynak [Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde bu örnek için kaynak belge oluşturma yönergelerini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7668f-129">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="7668f-130">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7668f-130">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="7668f-131"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="7668f-131">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="7668f-132">Bu örnek, [kaynak Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="7668f-132">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```output  
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
  
## <a name="next-steps"></a><span data-ttu-id="7668f-133">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="7668f-133">Next Steps</span></span>  
 <span data-ttu-id="7668f-134">Bir sonraki konu başlığında, [paragrafların metnini (C#) alırken](./retrieving-the-text-of-the-paragraphs.md), paragrafların metnini almak için bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7668f-134">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7668f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7668f-135">See also</span></span>

- [<span data-ttu-id="7668f-136">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="7668f-136">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)

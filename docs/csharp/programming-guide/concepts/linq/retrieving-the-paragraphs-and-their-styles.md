---
title: Paragrafları ve Stillerinin Alınması (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 47127b6f1d6bfaa0d8d93333882a0d0b59f1bae6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168303"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="52649-102">Paragrafları ve Stillerinin Alınması (C#)</span><span class="sxs-lookup"><span data-stu-id="52649-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="52649-103">Bu örnekte, WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazarız.</span><span class="sxs-lookup"><span data-stu-id="52649-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="52649-104">Ayrıca her paragrafın stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="52649-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="52649-105">Bu sorgu, önceki örnekte varsayılan stil stilini stillistesinden alan [Varsayılan Paragraf Stilini (C#) bulma](./finding-the-default-paragraph-style.md)sorgusuüzerine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52649-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="52649-106">Bu bilgiler, sorgunun açıkça ayarlanmış bir stili olmayan paragrafların stilini tanımlayabilmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="52649-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="52649-107">Paragraf stilleri `w:pPr` öğe üzerinden ayarlanır; bir paragraf bu öğeyi içermiyorsa, varsayılan stil ile biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="52649-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="52649-108">Bu konu, sorgunun bazı parçalarının önemini açıklar, ardından sorguyu tam, çalışan bir örneğin parçası olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="52649-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52649-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="52649-109">Example</span></span>  
 <span data-ttu-id="52649-110">Belgedeki tüm paragrafları ve stilleri almak için sorgunun kaynağı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="52649-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="52649-111">Bu ifade, önceki örnekte, Varsayılan Paragraf [Stilini Bulma (C#)](./finding-the-default-paragraph-style.md)sorgusunun kaynağına benzer.</span><span class="sxs-lookup"><span data-stu-id="52649-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="52649-112">Temel fark, eksen yerine <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni <xref:System.Xml.Linq.XContainer.Elements%2A> kullanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="52649-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="52649-113">Sorgu ekseni <xref:System.Xml.Linq.XContainer.Descendants%2A> kullanır, çünkü bölümleri olan belgelerde paragraflar gövde öğesinin doğrudan alt öğesi olmayacaktır; bunun yerine, paragraflar hiyerarşide iki düzey aşağı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="52649-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="52649-114">Kodun <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni kullanarak, belgenin bölümleri kullanıp kullanmadığı üzerinde çalışacağız.</span><span class="sxs-lookup"><span data-stu-id="52649-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52649-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="52649-115">Example</span></span>  
 <span data-ttu-id="52649-116">Sorgu, stil `let` düğümü içeren öğeyi belirlemek için bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="52649-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="52649-117">Eleman yoksa, `styleNode` şu şekilde `null`ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="52649-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="52649-118">Yan `let` tümce <xref:System.Xml.Linq.XContainer.Elements%2A> önce adlı `pPr`tüm öğeleri bulmak <xref:System.Xml.Linq.Extensions.Elements%2A> için ekseni kullanır, `pStyle`sonra adlandırılmış <xref:System.Linq.Enumerable.FirstOrDefault%2A> tüm alt öğeleri bulmak için uzantı yöntemini kullanır ve son olarak koleksiyonu bir singleton'a dönüştürmek için standart sorgu işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="52649-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="52649-119">Koleksiyon boşsa, `styleNode` '' `null`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="52649-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="52649-120">`pStyle` Bu, soyundan gelen düğümü aramak için yararlı bir deyimdir.</span><span class="sxs-lookup"><span data-stu-id="52649-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="52649-121">`pPr` Alt düğüm yoksa, kod bir özel durum atarak başarısız ne de yok unutmayın; bunun `styleNode` yerine, `null`bu `let` maddenin istenilen davranışı , olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="52649-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="52649-122">Sorgu, iki üyeden `StyleName` oluşan anonim bir `ParagraphNode`türde bir koleksiyon ve .</span><span class="sxs-lookup"><span data-stu-id="52649-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52649-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="52649-123">Example</span></span>  
 <span data-ttu-id="52649-124">Bu örnek, bir WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="52649-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="52649-125">Ayrıca her paragrafın stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="52649-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="52649-126">Bu örnek, bu öğreticide önceki örneklere dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52649-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="52649-127">Yeni sorgu aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="52649-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="52649-128">[Kaynak Office Açık XML Belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bu örnek için kaynak belge oluşturmak için yönergeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52649-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="52649-129">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="52649-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="52649-130"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="52649-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="52649-131">Bu örnek, [Kaynak Office Açık XML Belgesi (C#) oluşturma'da](./creating-the-source-office-open-xml-document.md)açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="52649-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="52649-132">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="52649-132">Next Steps</span></span>  
 <span data-ttu-id="52649-133">Bir sonraki konu, [Paragrafmetni (C#) alma,](./retrieving-the-text-of-the-paragraphs.md)paragrafmetni almak için bir sorgu oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="52649-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52649-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52649-134">See also</span></span>

- [<span data-ttu-id="52649-135">Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)</span><span class="sxs-lookup"><span data-stu-id="52649-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)

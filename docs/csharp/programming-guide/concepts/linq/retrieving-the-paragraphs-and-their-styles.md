---
title: "Paragrafları ve bunların stilleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d7619ede02e9a384ddceec23a232a53de1dad0aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="597e6-102">Paragrafları ve bunların stilleri (C#)</span><span class="sxs-lookup"><span data-stu-id="597e6-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="597e6-103">Bu örnekte, paragraf düğümleri WordprocessingML belgeden alır bir sorgu yazın.</span><span class="sxs-lookup"><span data-stu-id="597e6-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="597e6-104">Ayrıca, her paragraf stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="597e6-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="597e6-105">Bu sorgu önceki örnekte, sorgu inşa edilmiştir [varsayılan paragraf stili (C#) bulma](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), stilleri listesinden varsayılan stilini alır.</span><span class="sxs-lookup"><span data-stu-id="597e6-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="597e6-106">Sorgu açıkça ayarlanmış bir stil yok paragrafları stilini bulabilmeniz bu bilgiler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="597e6-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="597e6-107">Paragraf stilleri aracılığıyla ayarlanır `w:pPr` öğesi; bir paragraf bu öğe içermiyorsa, varsayılan stiliyle biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="597e6-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="597e6-108">Bu konuda sorgunun bazı parçalar önemini açıklar ve ardından sorguyu eksiksiz, çalışan bir örnek bir parçası olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="597e6-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="597e6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="597e6-109">Example</span></span>  
 <span data-ttu-id="597e6-110">Bir belge ve bunların stiller tüm paragrafları almaya yönelik sorgu kaynağı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="597e6-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="597e6-111">Bu ifade önceki örnekte, sorgunun kaynağını benzer [varsayılan paragraf stil (C#) bulma](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="597e6-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="597e6-112">İkisi arasındaki temel fark, kullanmasıdır <xref:System.Xml.Linq.XContainer.Descendants%2A> yerine eksen <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni.</span><span class="sxs-lookup"><span data-stu-id="597e6-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="597e6-113">Sorgu kullanan <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen belgelerde, bölümler olduğundan paragrafları body öğesi doğrudan alt olmaz; bunun yerine, paragrafları iki düzey aşağı hiyerarşi içinde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="597e6-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="597e6-114">Kullanarak <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen, kod çalışır belge bölümleri desteklemediğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="597e6-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="597e6-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="597e6-115">Example</span></span>  
 <span data-ttu-id="597e6-116">Sorgu kullanan bir `let` stili düğümü içeren öğeyi belirlemek üzere yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="597e6-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="597e6-117">Hiçbir öğe yoksa, ardından `styleNode` ayarlanır `null`:</span><span class="sxs-lookup"><span data-stu-id="597e6-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="597e6-118">`let` Yan tümcesi ilk kullanır <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksen `pPr`, sonra kullanır <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemi `pStyle`ve son olarak kullanan <xref:System.Linq.Enumerable.FirstOrDefault%2A> standart sorgu Koleksiyon bir tekliye dönüştürmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="597e6-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="597e6-119">Koleksiyon boş ise, `styleNode` ayarlanır `null`.</span><span class="sxs-lookup"><span data-stu-id="597e6-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="597e6-120">Aranacak yararlı bir deyim budur `pStyle` alt düğümü.</span><span class="sxs-lookup"><span data-stu-id="597e6-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="597e6-121">Unutmayın `pPr` kod mu ya da bir özel durum; atma tarafından başarısız alt düğüm yok, bunun yerine, `styleNode` ayarlanır `null`, bunun istediğiniz davranış olduğu `let` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="597e6-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="597e6-122">Anonim bir türün bir koleksiyon iki üyeleriyle sorgu projeleri `StyleName` ve `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="597e6-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="597e6-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="597e6-123">Example</span></span>  
 <span data-ttu-id="597e6-124">Bu örnek bir WordprocessingML belgeden paragraf düğümleri alınıyor WordprocessingML belgeye işler.</span><span class="sxs-lookup"><span data-stu-id="597e6-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="597e6-125">Ayrıca, her paragraf stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="597e6-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="597e6-126">Bu örnek önceki örnekler üzerinde Bu öğreticide oluşturur.</span><span class="sxs-lookup"><span data-stu-id="597e6-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="597e6-127">Yeni sorgu aşağıdaki kodu açıklamalarda belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="597e6-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="597e6-128">Bu örnekte, kaynak belge oluşturmak için yönergeler bulabilirsiniz [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="597e6-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="597e6-129">Bu örnek WindowsBase derlemesinde sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="597e6-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="597e6-130">Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="597e6-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="597e6-131">Bu örnek aşağıdaki açıklandığı belgeye uygulandığında çıktı üretir [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="597e6-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="597e6-132">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="597e6-132">Next Steps</span></span>  
 <span data-ttu-id="597e6-133">Sonraki konusunda [(C#) paragrafları metin alma](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), paragraf metni almak için bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="597e6-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597e6-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="597e6-134">See Also</span></span>  
 [<span data-ttu-id="597e6-135">Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)</span><span class="sxs-lookup"><span data-stu-id="597e6-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

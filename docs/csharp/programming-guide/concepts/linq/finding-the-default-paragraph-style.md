---
title: Varsayılan paragraf stilini bulma (C#)
description: C# ' de LINQ ile WordprocessingML belgesini nasıl işleyeceğini öğrenin. Bu örnek, belgedeki paragrafların varsayılan stilini bulur.
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e18bbbdbd5b2627c9ff4c3c3eedd84d7cb166a62
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103823"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="a02e6-104">Varsayılan paragraf stilini bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="a02e6-104">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="a02e6-105">WordprocessingML belgesi öğreticisindeki düzenleme bilgilerinde ilk görev, belgede varsayılan paragraf stilini bullevidir.</span><span class="sxs-lookup"><span data-stu-id="a02e6-105">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a02e6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a02e6-106">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a02e6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a02e6-107">Description</span></span>  
 <span data-ttu-id="a02e6-108">Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paketin belge ve stil parçalarını bulur ve ardından varsayılan stil adını bulan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="a02e6-108">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="a02e6-109">Office Open XML belge paketleri ve içerdikleri parçalar hakkında daha fazla bilgi için bkz. [Office Open XML WordprocessingML belgelerinin ayrıntıları (C#)](./wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="a02e6-109">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="a02e6-110">Sorgu, "paragraf" değeri ile adlandırılmış bir özniteliği olan adlı bir düğümü bulur `w:style` `w:type` ve ayrıca `w:default` "1" değerine sahip adlı bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a02e6-110">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="a02e6-111">Bu özniteliklere sahip yalnızca bir XML düğümü olacağı için, sorgu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> işleci kullanarak bir koleksiyonu tek bir öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a02e6-111">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="a02e6-112">Daha sonra, adlı özniteliğin değerini alır `w:styleId` .</span><span class="sxs-lookup"><span data-stu-id="a02e6-112">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="a02e6-113">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="a02e6-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="a02e6-114"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a02e6-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a02e6-115">Kod</span><span class="sxs-lookup"><span data-stu-id="a02e6-115">Code</span></span>  
  
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
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a><span data-ttu-id="a02e6-116">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="a02e6-116">Comments</span></span>  
 <span data-ttu-id="a02e6-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a02e6-117">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="a02e6-118">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a02e6-118">Next Steps</span></span>  
 <span data-ttu-id="a02e6-119">Sonraki örnekte, bir belgedeki ve stillerinin tüm paragraflarını bulan benzer bir sorgu oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="a02e6-119">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="a02e6-120">Paragrafları ve stillerini alma (C#)</span><span class="sxs-lookup"><span data-stu-id="a02e6-120">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  

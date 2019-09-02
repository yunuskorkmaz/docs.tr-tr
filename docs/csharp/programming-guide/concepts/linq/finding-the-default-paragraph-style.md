---
title: Varsayılan paragraf stilini bulma (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 45a3e293a88fc0d7fc6aa70d21d1d3a6a8bb9b13
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204109"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="ef7c1-102">Varsayılan paragraf stilini bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="ef7c1-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="ef7c1-103">WordprocessingML belgesi öğreticisindeki düzenleme bilgilerinde ilk görev, belgede varsayılan paragraf stilini bullevidir.</span><span class="sxs-lookup"><span data-stu-id="ef7c1-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef7c1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef7c1-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ef7c1-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef7c1-105">Description</span></span>  
 <span data-ttu-id="ef7c1-106">Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paketin belge ve stil parçalarını bulur ve ardından varsayılan stil adını bulan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="ef7c1-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="ef7c1-107">Office Open XML belge paketleri ve içerdikleri parçalar hakkında daha fazla bilgi için bkz. [Office Open XML WordprocessingML belgelerinin ayrıntıları (C#)](./wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="ef7c1-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="ef7c1-108">Sorgu, "paragraf" değeri `w:style` `w:type` ile adlandırılmış bir özniteliği olan adlı bir düğümü bulur ve ayrıca "1" değerine sahip adlı `w:default` bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ef7c1-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="ef7c1-109">Bu özniteliklere sahip yalnızca bir XML düğümü olacağı için, sorgu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> işleci kullanarak bir koleksiyonu tek bir öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ef7c1-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="ef7c1-110">Daha sonra, adlı `w:styleId`özniteliğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="ef7c1-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="ef7c1-111">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef7c1-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="ef7c1-112"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef7c1-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ef7c1-113">Kod</span><span class="sxs-lookup"><span data-stu-id="ef7c1-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="ef7c1-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef7c1-114">Comments</span></span>  
 <span data-ttu-id="ef7c1-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ef7c1-115">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="ef7c1-116">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="ef7c1-116">Next Steps</span></span>  
 <span data-ttu-id="ef7c1-117">Sonraki örnekte, bir belgedeki ve stillerinin tüm paragraflarını bulan benzer bir sorgu oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="ef7c1-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="ef7c1-118">Paragrafları ve stillerini alma (C#)</span><span class="sxs-lookup"><span data-stu-id="ef7c1-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  

---
title: Varsayılan Paragraf Stilini Bulma (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 8cc1f1b9df208b0b180e5fe4a50922b5ee46b480
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169538"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="48ec8-102">Varsayılan Paragraf Stilini Bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="48ec8-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="48ec8-103">WordprocessingML Belge öğreticisinde Bilgileri Manipüle Etme'deki ilk görev, belgedeki paragrafların varsayılan stilini bulmaktır.</span><span class="sxs-lookup"><span data-stu-id="48ec8-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48ec8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="48ec8-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="48ec8-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48ec8-105">Description</span></span>  
 <span data-ttu-id="48ec8-106">Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesini açar, belgeve stil bölümlerini bulur ve sonra varsayılan stil adını bulan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="48ec8-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="48ec8-107">Office Open XML belge paketleri ve bunların oluşan bölümleri hakkında bilgi [için](./wordprocessingml-document-with-styles.md)Bkz.</span><span class="sxs-lookup"><span data-stu-id="48ec8-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="48ec8-108">Sorgu, "paragraf" `w:style` değeriyle adında `w:type` bir özniteliği olan ve "1" değeriyle `w:default` de adlandırılan bir özniteliği olan bir düğüm bulur.</span><span class="sxs-lookup"><span data-stu-id="48ec8-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="48ec8-109">Bu özniteliklere sahip yalnızca bir XML düğümü olacağından, sorgu bir koleksiyonu singletona dönüştürmek için <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="48ec8-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="48ec8-110">Daha sonra özniteliğin değerini adı `w:styleId`ile alır.</span><span class="sxs-lookup"><span data-stu-id="48ec8-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="48ec8-111">Bu örnek, WindowsBase derlemesi sınıflarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="48ec8-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="48ec8-112"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="48ec8-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48ec8-113">Kod</span><span class="sxs-lookup"><span data-stu-id="48ec8-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="48ec8-114">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="48ec8-114">Comments</span></span>  
 <span data-ttu-id="48ec8-115">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="48ec8-115">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="48ec8-116">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="48ec8-116">Next Steps</span></span>  
 <span data-ttu-id="48ec8-117">Sonraki örnekte, belgedeki tüm paragrafları ve stillerini bulan benzer bir sorgu oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="48ec8-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="48ec8-118">Paragrafları ve Stillerinin Alınması (C#)</span><span class="sxs-lookup"><span data-stu-id="48ec8-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  

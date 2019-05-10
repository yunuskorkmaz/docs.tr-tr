---
title: Varsayılan paragraf stilini (C#) bulma
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 89c70fcbc9d5286e2c9381250b30d525ebb1eb36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596691"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="b4e2d-102">Varsayılan paragraf stilini (C#) bulma</span><span class="sxs-lookup"><span data-stu-id="b4e2d-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="b4e2d-103">WordprocessingML belgesinin öğreticide düzenleme bilgileri ilk görevi, belgede varsayılan paragraf stilini bulmaktır.</span><span class="sxs-lookup"><span data-stu-id="b4e2d-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4e2d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4e2d-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b4e2d-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4e2d-105">Description</span></span>  
 <span data-ttu-id="b4e2d-106">Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paket belge ve stil bölümlerini bulur ve ardından varsayılan stil adı bulan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="b4e2d-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="b4e2d-107">Office Open XML belge paketler ve oluşmalıdır ve parçaları hakkında daha fazla bilgi için bkz. [ayrıntıları, Office Open XML WordprocessingML belgelerinin (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="b4e2d-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="b4e2d-108">Sorgunun bulacağı adlı bir düğüm `w:style` adlı bir öznitelik olan `w:type` "paragraf" değerini ve ayrıca sahip bir öznitelik adlandırılmış `w:default` değerini "1" ile.</span><span class="sxs-lookup"><span data-stu-id="b4e2d-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="b4e2d-109">Sorgu kullanır, bu öznitelikleri yalnızca bir XML düğümüyle olacaktır çünkü <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> için tek bir koleksiyon dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="b4e2d-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="b4e2d-110">Ardından bir ada sahip bir öznitelik değerini alır `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="b4e2d-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="b4e2d-111">Bu örnek WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4e2d-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="b4e2d-112">Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b4e2d-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b4e2d-113">Kod</span><span class="sxs-lookup"><span data-stu-id="b4e2d-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="b4e2d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4e2d-114">Comments</span></span>  
 <span data-ttu-id="b4e2d-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b4e2d-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="b4e2d-116">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b4e2d-116">Next Steps</span></span>  
 <span data-ttu-id="b4e2d-117">Sonraki örnekte, bir belge ve stillerini paragraflar bulur benzer bir sorgu oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="b4e2d-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="b4e2d-118">Paragrafları ve stillerini (C#) alma</span><span class="sxs-lookup"><span data-stu-id="b4e2d-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4e2d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4e2d-119">See also</span></span>

- [<span data-ttu-id="b4e2d-120">Öğretici: WordprocessingML belgesindeki içeriği düzenleme</span><span class="sxs-lookup"><span data-stu-id="b4e2d-120">Tutorial: Manipulating Content in a WordprocessingML Document</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

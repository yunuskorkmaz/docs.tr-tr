---
title: Office Açık XML belge bölümleri (C#) çıkarır örneği
ms.date: 07/20/2015
ms.assetid: 6cd37055-89b4-42e8-bf27-5a29717e35f3
ms.openlocfilehash: e63f6eafb32a6426d6c3fd7296c0e8fa6595efee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325376"
---
# <a name="example-that-outputs-office-open-xml-document-parts-c"></a><span data-ttu-id="e4ec8-102">Office Açık XML belge bölümleri (C#) çıkarır örneği</span><span class="sxs-lookup"><span data-stu-id="e4ec8-102">Example that Outputs Office Open XML Document Parts (C#)</span></span>
<span data-ttu-id="e4ec8-103">Bu konuda, bir Office Açık XML belgesi Aç ve erişim içindeki bölümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-103">This topic shows how to open an Office Open XML document and access parts within it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4ec8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4ec8-104">Example</span></span>  
 <span data-ttu-id="e4ec8-105">Aşağıdaki örnek, bir Office Açık XML belge açılır ve belge ve stil bölümlerini konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-105">The following example opens an Office Open XML document, and prints the document part and the style part to the console.</span></span>  
  
 <span data-ttu-id="e4ec8-106">Bu örnek WindowsBase derlemeden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-106">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="e4ec8-107">Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-107">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
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
        XDocument xdoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        Console.WriteLine("TargetUri:{0}", docPackageRelationship.TargetUri);  
        Console.WriteLine("==================================================================");  
        Console.WriteLine(xdoc.Root);  
        Console.WriteLine();  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            XDocument styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
  
            Console.WriteLine("TargetUri:{0}", styleRelation.TargetUri);  
            Console.WriteLine("==================================================================");  
            Console.WriteLine(styleDoc.Root);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4ec8-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-108">See Also</span></span>  
 [<span data-ttu-id="e4ec8-109">Ayrıntılar Office Açık XML WordprocessingML belgeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="e4ec8-109">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)

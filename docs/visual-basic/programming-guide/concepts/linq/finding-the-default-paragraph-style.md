---
title: Varsayılan paragraf stilini bulma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 6754c48148e81b02eb8c63843b57bc3d28a5774a
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352891"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="ee7ec-102">Varsayılan paragraf stilini bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee7ec-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="ee7ec-103">WordprocessingML belgesi öğreticisindeki düzenleme bilgilerinde ilk görev, belgede varsayılan paragraf stilini bullevidir.</span><span class="sxs-lookup"><span data-stu-id="ee7ec-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee7ec-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee7ec-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ee7ec-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee7ec-105">Description</span></span>  
 <span data-ttu-id="ee7ec-106">Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paketin belge ve stil parçalarını bulur ve ardından varsayılan stil adını bulan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="ee7ec-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="ee7ec-107">Office Open XML belge paketleri ve içerdikleri parçalar hakkında daha fazla bilgi için bkz. [Office Open XML WordprocessingML belgelerinin ayrıntıları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="ee7ec-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="ee7ec-108">Sorgu, "paragraf" değerine sahip `w:type` adlı ve ayrıca "1" değerine sahip `w:default` adlı bir özniteliğe sahip `w:style` adlı bir düğüm bulur.</span><span class="sxs-lookup"><span data-stu-id="ee7ec-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="ee7ec-109">Bu özniteliklere sahip yalnızca bir XML düğümü olacağı için, sorgu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> işlecini kullanarak bir koleksiyonu tek başına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ee7ec-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="ee7ec-110">Daha sonra `w:styleId` adlı özniteliğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="ee7ec-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="ee7ec-111">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee7ec-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="ee7ec-112">@No__t-0 ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee7ec-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ee7ec-113">Kod</span><span class="sxs-lookup"><span data-stu-id="ee7ec-113">Code</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="ee7ec-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee7ec-114">Comments</span></span>  
 <span data-ttu-id="ee7ec-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ee7ec-115">This example produces the following output:</span></span>  
  
```console  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="ee7ec-116">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="ee7ec-116">Next Steps</span></span>  
 <span data-ttu-id="ee7ec-117">Sonraki örnekte, bir belgedeki ve stillerinin tüm paragraflarını bulan benzer bir sorgu oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="ee7ec-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="ee7ec-118">Paragrafları ve stillerini alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee7ec-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee7ec-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee7ec-119">See also</span></span>

- [<span data-ttu-id="ee7ec-120">Öğretici: WordprocessingML belgesinde Içerik işleme (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="ee7ec-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

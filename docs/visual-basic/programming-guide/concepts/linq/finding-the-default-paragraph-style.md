---
title: (Visual Basic) varsayılan paragraf stilini bulma
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 0694c9144e44e4a5de262f97581eb18943937243
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931319"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="909e7-102">(Visual Basic) varsayılan paragraf stilini bulma</span><span class="sxs-lookup"><span data-stu-id="909e7-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="909e7-103">WordprocessingML belgesinin öğreticide düzenleme bilgileri ilk görevi, belgede varsayılan paragraf stilini bulmaktır.</span><span class="sxs-lookup"><span data-stu-id="909e7-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="909e7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="909e7-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="909e7-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="909e7-105">Description</span></span>  
 <span data-ttu-id="909e7-106">Aşağıdaki örnek, bir Office Open XML WordprocessingML belgesi açar, paket belge ve stil bölümlerini bulur ve ardından varsayılan stil adı bulan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="909e7-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="909e7-107">Office Open XML belge paketler ve oluşmalıdır ve parçaları hakkında daha fazla bilgi için bkz. [ayrıntıları, Office Open XML WordprocessingML belgelerinin (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="909e7-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="909e7-108">Sorgunun bulacağı adlı bir düğüm `w:style` adlı bir öznitelik olan `w:type` "paragraf" değerini ve ayrıca sahip bir öznitelik adlandırılmış `w:default` değerini "1" ile.</span><span class="sxs-lookup"><span data-stu-id="909e7-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="909e7-109">Sorgu kullanır, bu öznitelikleri yalnızca bir XML düğümüyle olacaktır çünkü <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> için tek bir koleksiyon dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="909e7-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="909e7-110">Ardından bir ada sahip bir öznitelik değerini alır `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="909e7-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="909e7-111">Bu örnek WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="909e7-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="909e7-112">Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="909e7-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="909e7-113">Kod</span><span class="sxs-lookup"><span data-stu-id="909e7-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="909e7-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="909e7-114">Comments</span></span>  
 <span data-ttu-id="909e7-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="909e7-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="909e7-116">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="909e7-116">Next Steps</span></span>  
 <span data-ttu-id="909e7-117">Sonraki örnekte, bir belge ve stillerini paragraflar bulur benzer bir sorgu oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="909e7-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="909e7-118">Paragrafları ve stillerini (Visual Basic) alma</span><span class="sxs-lookup"><span data-stu-id="909e7-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="909e7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="909e7-119">See also</span></span>

- [<span data-ttu-id="909e7-120">Öğretici: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme</span><span class="sxs-lookup"><span data-stu-id="909e7-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

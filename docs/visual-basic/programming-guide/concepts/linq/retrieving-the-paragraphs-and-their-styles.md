---
title: Paragrafları ve stillerini (Visual Basic) alma
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 3c6554c44c95db13aada0d9edf96cc2df595c6d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816947"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="fd904-102">Paragrafları ve stillerini (Visual Basic) alma</span><span class="sxs-lookup"><span data-stu-id="fd904-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="fd904-103">Bu örnekte biz WordprocessingML belgeden paragraf düğümleri alan bir sorgu yazın.</span><span class="sxs-lookup"><span data-stu-id="fd904-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="fd904-104">Ayrıca, her bir paragraf stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fd904-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="fd904-105">Bu sorgu önceki örnekte, sorguda geliştirir [(Visual Basic) varsayılan paragraf stilini bulma](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), stilleri listesinden varsayılan stilini alır.</span><span class="sxs-lookup"><span data-stu-id="fd904-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="fd904-106">Bu bilgiler, böylece sorgu açıkça ayarlanmış bir stil sahip değil paragraflar stilini gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fd904-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="fd904-107">Stilleri aracılığıyla ayarlanır `w:pPr` öğesi; bir paragraf bu öğe içermiyorsa varsayılan stili ile biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fd904-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="fd904-108">Bu konuda bazı parçalar sorgunun önemini açıklar ve ardından sorguyu eksiksiz, çalışan bir örnek bir parçası olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd904-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd904-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd904-109">Example</span></span>  
 <span data-ttu-id="fd904-110">Bir belge ve stillerini tüm paragraflarda almaya yönelik sorgu kaynağı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fd904-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="fd904-111">Bu ifade, önceki örnekte, sorgunun kaynak benzerdir [(Visual Basic) varsayılan paragraf stilini bulma](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="fd904-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="fd904-112">İkisi arasındaki temel fark, kullanmasıdır <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yerine <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni.</span><span class="sxs-lookup"><span data-stu-id="fd904-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="fd904-113">Sorgu kullanan <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen paragrafları belgeleri, bölüm olduğundan gövde öğesinin doğrudan alt olmaz; bunun yerine, paragraf iki düzeyi aşağı hiyerarşide olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fd904-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="fd904-114">Kullanarak <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen, kod çalışır belgenin bölüm olup olmadığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd904-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd904-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd904-115">Example</span></span>  
 <span data-ttu-id="fd904-116">Sorgu kullanan bir `Let` stil düğümü içeren öğe belirlemek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fd904-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="fd904-117">Hiçbir öğe yoksa, ardından `styleNode` ayarlanır `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="fd904-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="fd904-118">`Let` Yan tümcesinin ilk kullanır <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksen `pPr`, ardından kullanır <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemi `pStyle`ve son olarak kullanan <xref:System.Linq.Enumerable.FirstOrDefault%2A> standart sorgu koleksiyon için bir singleton dönüştürmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="fd904-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="fd904-119">Koleksiyon boşsa, `styleNode` ayarlanır `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fd904-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="fd904-120">Aramak için kullanışlı bir deyim budur `pStyle` alt düğümü.</span><span class="sxs-lookup"><span data-stu-id="fd904-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="fd904-121">Unutmayın `pPr` alt düğüm mevcut değil, kod yok ya da; özel durum ile başarısız oluyor bunun yerine, `styleNode` ayarlanır `Nothing`, istenen davranışı olduğu `Let` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fd904-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="fd904-122">Anonim bir türün bir koleksiyon iki üyeli sorgu projeleri `StyleName` ve `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="fd904-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd904-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd904-123">Example</span></span>  
 <span data-ttu-id="fd904-124">Bu örnekte, paragraf düğümleri WordprocessingML belge alınırken WordprocessingML belgesinin işler.</span><span class="sxs-lookup"><span data-stu-id="fd904-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="fd904-125">Ayrıca, her bir paragraf stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fd904-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="fd904-126">Bu örnek, önceki örneklerde üzerinde Bu öğreticide oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd904-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="fd904-127">Yeni sorgu aşağıdaki kod açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fd904-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="fd904-128">Bu örnekte için kaynak belge oluşturma için yönergeler bulabilirsiniz [kaynak Office Open XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="fd904-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="fd904-129">Bu örnekte WindowsBase derlemede bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd904-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="fd904-130">Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fd904-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fd904-131">Bu örnek aşağıdaki belgede açıklanan uygulandığında çıktıyı üretir [kaynak Office Open XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="fd904-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="fd904-132">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="fd904-132">Next Steps</span></span>  
 <span data-ttu-id="fd904-133">Bir sonraki konu başlığında [(Visual Basic) paragrafların metnini alma](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), paragraf metnini almak için bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fd904-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd904-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd904-134">See also</span></span>

- [<span data-ttu-id="fd904-135">Öğretici: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme</span><span class="sxs-lookup"><span data-stu-id="fd904-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

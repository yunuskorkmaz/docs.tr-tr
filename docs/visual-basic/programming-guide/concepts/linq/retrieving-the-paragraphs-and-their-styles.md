---
title: Paragrafları ve bunların stilleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 5b8075b5aa05c32d2dc894149a8fa53f103138c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648313"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="44f4e-102">Paragrafları ve bunların stilleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44f4e-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="44f4e-103">Bu örnekte, paragraf düğümleri WordprocessingML belgeden alır bir sorgu yazın.</span><span class="sxs-lookup"><span data-stu-id="44f4e-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="44f4e-104">Ayrıca, her paragraf stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44f4e-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="44f4e-105">Bu sorgu önceki örnekte, sorgu inşa edilmiştir [varsayılan paragraf stili (Visual Basic) bulma](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), stilleri listesinden varsayılan stilini alır.</span><span class="sxs-lookup"><span data-stu-id="44f4e-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="44f4e-106">Sorgu açıkça ayarlanmış bir stil yok paragrafları stilini bulabilmeniz bu bilgiler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="44f4e-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="44f4e-107">Paragraf stilleri aracılığıyla ayarlanır `w:pPr` öğesi; bir paragraf bu öğe içermiyorsa, varsayılan stiliyle biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="44f4e-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="44f4e-108">Bu konuda sorgunun bazı parçalar önemini açıklar ve ardından sorguyu eksiksiz, çalışan bir örnek bir parçası olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="44f4e-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f4e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="44f4e-109">Example</span></span>  
 <span data-ttu-id="44f4e-110">Bir belge ve bunların stiller tüm paragrafları almaya yönelik sorgu kaynağı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="44f4e-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="44f4e-111">Bu ifade önceki örnekte, sorgunun kaynağını benzer [varsayılan paragraf stil (Visual Basic) bulma](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="44f4e-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="44f4e-112">İkisi arasındaki temel fark, kullanmasıdır <xref:System.Xml.Linq.XContainer.Descendants%2A> yerine eksen <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni.</span><span class="sxs-lookup"><span data-stu-id="44f4e-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="44f4e-113">Sorgu kullanan <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen belgelerde, bölümler olduğundan paragrafları body öğesi doğrudan alt olmaz; bunun yerine, paragrafları iki düzey aşağı hiyerarşi içinde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="44f4e-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="44f4e-114">Kullanarak <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen, kod çalışır belge bölümleri desteklemediğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44f4e-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f4e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="44f4e-115">Example</span></span>  
 <span data-ttu-id="44f4e-116">Sorgu kullanan bir `Let` stili düğümü içeren öğeyi belirlemek üzere yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="44f4e-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="44f4e-117">Hiçbir öğe yoksa, ardından `styleNode` ayarlanır `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="44f4e-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="44f4e-118">`Let` Yan tümcesi ilk kullanır <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksen `pPr`, sonra kullanır <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemi `pStyle`ve son olarak kullanan <xref:System.Linq.Enumerable.FirstOrDefault%2A> standart sorgu Koleksiyon bir tekliye dönüştürmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="44f4e-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="44f4e-119">Koleksiyon boş ise, `styleNode` ayarlanır `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="44f4e-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="44f4e-120">Aranacak yararlı bir deyim budur `pStyle` alt düğümü.</span><span class="sxs-lookup"><span data-stu-id="44f4e-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="44f4e-121">Unutmayın `pPr` kod mu ya da bir özel durum; atma tarafından başarısız alt düğüm yok, bunun yerine, `styleNode` ayarlanır `Nothing`, bunun istediğiniz davranış olduğu `Let` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="44f4e-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="44f4e-122">Anonim bir türün bir koleksiyon iki üyeleriyle sorgu projeleri `StyleName` ve `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="44f4e-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f4e-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="44f4e-123">Example</span></span>  
 <span data-ttu-id="44f4e-124">Bu örnek bir WordprocessingML belgeden paragraf düğümleri alınıyor WordprocessingML belgeye işler.</span><span class="sxs-lookup"><span data-stu-id="44f4e-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="44f4e-125">Ayrıca, her paragraf stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44f4e-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="44f4e-126">Bu örnek önceki örnekler üzerinde Bu öğreticide oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44f4e-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="44f4e-127">Yeni sorgu aşağıdaki kodu açıklamalarda belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="44f4e-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="44f4e-128">Bu örnekte, kaynak belge oluşturmak için yönergeler bulabilirsiniz [kaynak Office Açık XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="44f4e-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="44f4e-129">Bu örnek WindowsBase derlemesinde sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="44f4e-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="44f4e-130">Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="44f4e-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="44f4e-131">Bu örnek aşağıdaki açıklandığı belgeye uygulandığında çıktı üretir [kaynak Office Açık XML belgesi (Visual Basic) oluşturulmasını](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="44f4e-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="44f4e-132">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="44f4e-132">Next Steps</span></span>  
 <span data-ttu-id="44f4e-133">Sonraki konusunda [(Visual Basic) paragrafları metin alma](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), paragraf metni almak için bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="44f4e-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f4e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44f4e-134">See Also</span></span>  
 [<span data-ttu-id="44f4e-135">Öğretici: Düzenleme içeriği WordprocessingML belgesinde (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44f4e-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

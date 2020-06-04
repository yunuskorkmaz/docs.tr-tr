---
title: Paragrafları ve Stillerini Alma
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413420"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="0f5e5-102">Paragrafları ve stillerini alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f5e5-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="0f5e5-103">Bu örnekte, bir WordprocessingML belgesinden paragraf düğümlerini alan bir sorgu yazdık.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="0f5e5-104">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="0f5e5-105">Bu sorgu, stil listesinden varsayılan stili alan [varsayılan paragraf stilini (Visual Basic) bularak](finding-the-default-paragraph-style.md), önceki örnekteki sorgu üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="0f5e5-106">Bu bilgiler, sorgunun açıkça ayarlanmış bir stile sahip olmayan paragrafların stilini belirleyebilmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="0f5e5-107">Paragraf stilleri öğe aracılığıyla ayarlanır `w:pPr` ; bir paragraf bu öğeyi içermiyorsa, varsayılan stille biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="0f5e5-108">Bu konuda, sorgunun bazı parçalarının önemi açıklanmakta ve sorgu tam, çalışan bir örnek kapsamında gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5e5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f5e5-109">Example</span></span>  
 <span data-ttu-id="0f5e5-110">Belgedeki tüm paragrafları ve bunların stillerini almak için sorgunun kaynağı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0f5e5-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="0f5e5-111">Bu ifade, önceki örnekteki sorgunun kaynağına benzer, [varsayılan paragraf stilini (Visual Basic) buluyor](finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="0f5e5-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="0f5e5-112">Temel fark, <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yerine eksenin kullanıldığı bir değer <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="0f5e5-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="0f5e5-113">Sorgu, bölümleri bulunan <xref:System.Xml.Linq.XContainer.Descendants%2A> belgelerde, paragrafları, gövde öğesinin doğrudan alt öğeleri olmayacak şekilde kullanır; bunun yerine, paragraflar hiyerarşide iki düzey olur.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="0f5e5-114"><xref:System.Xml.Linq.XContainer.Descendants%2A>Eksen kullanılarak, kod belgenin bölüm kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5e5-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f5e5-115">Example</span></span>  
 <span data-ttu-id="0f5e5-116">Sorgu, `Let` Stil düğümünü içeren öğeyi belirlemede bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="0f5e5-117">Öğe yoksa, şu `styleNode` şekilde ayarlanır `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="0f5e5-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="0f5e5-118">`Let`Yan tümcesi ilk olarak <xref:System.Xml.Linq.XContainer.Elements%2A> adlı tüm öğeleri bulmak için eksenini kullanır `pPr` , ardından <xref:System.Xml.Linq.Extensions.Elements%2A> adlı tüm alt öğeleri bulmak için genişletme yöntemini kullanır `pStyle` ve son olarak, <xref:System.Linq.Enumerable.FirstOrDefault%2A> koleksiyonu tek bir tekil öğesine dönüştürmek için standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="0f5e5-119">Koleksiyon boşsa, `styleNode` olarak ayarlanır `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="0f5e5-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="0f5e5-120">Bu, alt düğümü aramak için kullanışlı bir deyimdir `pStyle` .</span><span class="sxs-lookup"><span data-stu-id="0f5e5-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="0f5e5-121">`pPr`Alt düğüm yoksa, bir özel durum oluşturarak kodun bir istisna olduğunu veya başarısız olduğunu, bunun yerine, `styleNode` `Nothing` Bu yan tümcesinin istenen davranışı olan olarak ayarlandığını unutmayın `Let` .</span><span class="sxs-lookup"><span data-stu-id="0f5e5-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="0f5e5-122">Sorgu, iki üyeli anonim bir türün bir koleksiyonunu `StyleName` ve `ParagraphNode` .</span><span class="sxs-lookup"><span data-stu-id="0f5e5-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5e5-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f5e5-123">Example</span></span>  
 <span data-ttu-id="0f5e5-124">Bu örnek, WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="0f5e5-125">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="0f5e5-126">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="0f5e5-127">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="0f5e5-128">Kaynak [Office Open XML belgesi (Visual Basic) oluşturma](creating-the-source-office-open-xml-document.md)bölümünde bu örnek için kaynak belge oluşturma yönergelerini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="0f5e5-129">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="0f5e5-130"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="0f5e5-131">Bu örnek, [kaynak Office Open XML belgesi (Visual Basic) oluşturma](creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
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
  
## <a name="next-steps"></a><span data-ttu-id="0f5e5-132">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="0f5e5-132">Next Steps</span></span>  
 <span data-ttu-id="0f5e5-133">Bir sonraki konu başlığında, [paragrafların metnini (Visual Basic) alırken](retrieving-the-text-of-the-paragraphs.md), paragrafların metnini almak için bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f5e5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f5e5-134">See also</span></span>

- [<span data-ttu-id="0f5e5-135">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f5e5-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)

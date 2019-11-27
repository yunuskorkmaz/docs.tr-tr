---
title: Paragrafların Metnini Alma
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 596a6548f45d82c7ae260f9b010d2f139eb1c1fa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347522"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="48441-102">Paragrafların metnini alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48441-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="48441-103">Bu örnek, önceki örnekte yer alan, [paragrafları ve stillerini (Visual Basic) alırken](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="48441-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="48441-104">Bu yeni örnek, her bir paragrafın metnini dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="48441-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="48441-105">Bu örnek, metni almak için, anonim türler koleksiyonu aracılığıyla yinelenen bir sorgu ekler ve yeni bir üyenin eklenmesiyle adsız bir türün yeni bir koleksiyonunu `Text`.</span><span class="sxs-lookup"><span data-stu-id="48441-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="48441-106">Birden çok dizeyi tek bir dizede birleştirmek için <xref:System.Linq.Enumerable.Aggregate%2A> standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="48441-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="48441-107">Bu teknik (yani, ilk olarak anonim bir türün koleksiyonuna yansıtırken, daha sonra bu koleksiyonun yeni bir anonim tür koleksiyonuna proje için kullanılması) ortak ve kullanışlı bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="48441-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="48441-108">Bu sorgu, ilk anonim türe yansıtılamadan yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="48441-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="48441-109">Ancak, yavaş değerlendirme nedeniyle bunu yapmak çok daha fazla işlem gücü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="48441-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="48441-110">Deyim yığında daha kısa süreli nesneler oluşturur, ancak bu durum performansı önemli ölçüde düşürür.</span><span class="sxs-lookup"><span data-stu-id="48441-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="48441-111">Tabii ki, paragrafları alma işlevini, her bir paragrafın stilini ve her bir paragrafın metnini içeren tek bir sorgu yazmak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="48441-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="48441-112">Ancak, sonuçta elde edilen kod daha modüler ve bakımını daha kolay olduğundan, genellikle daha karmaşık bir sorguyu birden çok sorguya bölmek faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="48441-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="48441-113">Ayrıca, sorgunun bir bölümünü yeniden kullanmanız gerekiyorsa, sorgular bu şekilde yazılmışsa yeniden düzenleme daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="48441-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="48441-114">Birlikte zincirleme olan bu sorgular, " [ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)konusundaki ayrıntılı olarak incelenen işleme modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="48441-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48441-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="48441-115">Example</span></span>  
 <span data-ttu-id="48441-116">Bu örnekte, bir WordprocessingML belgesi işlenir, öğe düğümü, stil adı ve her paragrafın metni belirlenir.</span><span class="sxs-lookup"><span data-stu-id="48441-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="48441-117">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="48441-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="48441-118">Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="48441-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="48441-119">Bu örnek için kaynak belge oluşturmaya ilişkin yönergeler için bkz. [kaynak Office Open XML belgesi oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="48441-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="48441-120">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="48441-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="48441-121"><xref:System.IO.Packaging?displayProperty=nameWithType> ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="48441-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because VB does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
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
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Following is the new query that retrieves the text of  
        ' each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t> _  
                    .Aggregate(New StringBuilder(), _  
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _  
                               Function(s As StringBuilder) s.ToString) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="48441-122">Bu örnek, [kaynak Office Open XML belgesi (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="48441-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >Imports System<  
StyleName:Code ><  
StyleName:Code >Class Program<  
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >   End Sub<  
StyleName:Code >End Class<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="48441-123">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="48441-123">Next Steps</span></span>  
 <span data-ttu-id="48441-124">Sonraki örnek, birden çok dizeyi tek bir dizeye birleştirmek için <xref:System.Linq.Enumerable.Aggregate%2A>yerine bir genişletme yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="48441-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="48441-125">Bir genişletme yöntemi kullanarak yeniden düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48441-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="48441-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48441-126">See also</span></span>

- [<span data-ttu-id="48441-127">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48441-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="48441-128">LINQ to XML ertelenmiş yürütme ve geç değerlendirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48441-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

---
title: XML Değişmez Değerlerinde Boşluk (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 60ee90c69aeda38f95107a6043801a4994972079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649756"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="88647-102">XML Değişmez Değerlerinde Boşluk (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88647-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="88647-103">Visual Basic derleyici oluştururken bir XML değişmez değeri yalnızca önemli boşluk karakterlerinden içerir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesi.</span><span class="sxs-lookup"><span data-stu-id="88647-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="88647-104">Önemsiz boşluk karakterleri dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="88647-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="88647-105">Önemli ve önemsiz beyaz alan</span><span class="sxs-lookup"><span data-stu-id="88647-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="88647-106">XML değişmez değerlerinde boşluk karakterleri yalnızca üç alana önemlidir:</span><span class="sxs-lookup"><span data-stu-id="88647-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="88647-107">Bir öznitelik değeri olduklarında.</span><span class="sxs-lookup"><span data-stu-id="88647-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="88647-108">Ne zaman bir öğenin metin içeriğini parçasıdır ve metin ayrıca diğer karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="88647-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="88647-109">Bir öğenin metin içeriği katıştırılmış bir ifadede olduklarında.</span><span class="sxs-lookup"><span data-stu-id="88647-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="88647-110">Aksi takdirde derleyici boşluk karakterleri önemsiz olarak değerlendirir ve ardından eklememeyi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değeri için nesnesi.</span><span class="sxs-lookup"><span data-stu-id="88647-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="88647-111">XML değişmez değer anlamsız boşluk eklemek için bir boşluk ile değişmez dize değeri içeren katıştırılmış ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="88647-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88647-112">Varsa `xml:space` özniteliği görünür bir XML öğesi değişmez değeri, Visual Basic derleyici özniteliğinde içeren <xref:System.Xml.Linq.XElement> nesnesi, ancak bu öznitelik derleyici boşluk nasıl işler değiştirmez ekleme.</span><span class="sxs-lookup"><span data-stu-id="88647-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="88647-113">Örnekler</span><span class="sxs-lookup"><span data-stu-id="88647-113">Examples</span></span>  
 <span data-ttu-id="88647-114">Aşağıdaki örnek, dış ve iç iki XML öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="88647-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="88647-115">Her iki öğeler, metin içeriğini boşluk içerir.</span><span class="sxs-lookup"><span data-stu-id="88647-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="88647-116">Boşluk Dış öğede yalnızca boşluk ve bir XML öğesi içerdiğinden önemsizdir.</span><span class="sxs-lookup"><span data-stu-id="88647-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="88647-117">Boşluk iç öğesinde, boşluk ve metin içerdiği için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="88647-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="88647-118">Bu kodu çalıştırdığınızda, aşağıdaki metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88647-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88647-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88647-119">See Also</span></span>  
 [<span data-ttu-id="88647-120">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="88647-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

---
title: XML Değişmez Değerlerinde Boşluk (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: ef371a984d03485ccaf1ee5d61aa3cf39d80ef32
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979066"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="878d6-102">XML Değişmez Değerlerinde Boşluk (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="878d6-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="878d6-103">Oluştururken bir XML değişmez değeri yalnızca önemli boşluk karakterlerinden Visual Basic Derleyicisi içerir. bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne.</span><span class="sxs-lookup"><span data-stu-id="878d6-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="878d6-104">Önemsiz beyaz boşluk karakterleri dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="878d6-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="878d6-105">Önemli ve önemsiz boşluk</span><span class="sxs-lookup"><span data-stu-id="878d6-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="878d6-106">XML değişmez değerlerinde boşluk karakterleri yalnızca üç alanda büyük/küçük harf önemlidir:</span><span class="sxs-lookup"><span data-stu-id="878d6-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="878d6-107">Bir öznitelik değerinde olduklarında.</span><span class="sxs-lookup"><span data-stu-id="878d6-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="878d6-108">Bir öğenin metin içeriğini parçasıdır ve metin, ayrıca diğer karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="878d6-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="878d6-109">Bir öğenin metin içeriğini için katıştırılmış bir ifadede olduklarında.</span><span class="sxs-lookup"><span data-stu-id="878d6-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="878d6-110">Aksi halde, derleyici beyaz boşluk karakterleri önemsiz olarak değerlendirir ve ardından içinde içermez [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değer nesnesi.</span><span class="sxs-lookup"><span data-stu-id="878d6-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="878d6-111">XML değişmez değer Önemsiz boşluk eklemek için boşluk bir dize içeren bir katıştırılmış deyim kullanın.</span><span class="sxs-lookup"><span data-stu-id="878d6-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="878d6-112">Varsa `xml:space` özniteliği görünür bir XML öğesi değişmez değeri, öznitelik, Visual Basic Derleyicisi içerir <xref:System.Xml.Linq.XElement> nesne, ancak bu öznitelik derleyici boşluk nasıl işler değişmez ekleme.</span><span class="sxs-lookup"><span data-stu-id="878d6-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="878d6-113">Örnekler</span><span class="sxs-lookup"><span data-stu-id="878d6-113">Examples</span></span>  
 <span data-ttu-id="878d6-114">Aşağıdaki örnek, dış ve iç iki XML öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="878d6-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="878d6-115">Her iki öğe, metin içeriğini boşluk içerir.</span><span class="sxs-lookup"><span data-stu-id="878d6-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="878d6-116">Dış öğe boşluk, boşluk ve bir XML öğesinin içerdiği için önemsizdir.</span><span class="sxs-lookup"><span data-stu-id="878d6-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="878d6-117">İç öğe boşluk, boşluk ve metnin içerdiği için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="878d6-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="878d6-118">Bu kod, çalıştırdığınızda, aşağıdaki metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="878d6-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="878d6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="878d6-119">See also</span></span>
- [<span data-ttu-id="878d6-120">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="878d6-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

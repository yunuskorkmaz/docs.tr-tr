---
title: 'Nasıl yapılır: XML Alt Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392824"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="ee63a-102">Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee63a-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="ee63a-103">Bu örnek, bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee63a-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="ee63a-104">Özellikle, <xref:System.Xml.Linq.XElement.Value%2A> koleksiyonda `name` alt eksen özelliğinin döndürdüğü ilk öğenin değerini almak için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee63a-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="ee63a-105">`name`Alt eksen özelliği, nesnesinde adlı tüm alt öğeleri alır `phone` `contact` .</span><span class="sxs-lookup"><span data-stu-id="ee63a-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="ee63a-106">Bu örnek, `phone` nesnesinde bulunan adlı tüm alt öğelere erişmek için alt eksen özelliğini de kullanır `phone` `contact` .</span><span class="sxs-lookup"><span data-stu-id="ee63a-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee63a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee63a-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="ee63a-108">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="ee63a-108">Compile the code</span></span>  
 <span data-ttu-id="ee63a-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ee63a-109">This example requires:</span></span>  
  
- <span data-ttu-id="ee63a-110"><xref:System.Xml.Linq>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="ee63a-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee63a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee63a-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ee63a-112">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="ee63a-112">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="ee63a-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="ee63a-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="ee63a-114">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="ee63a-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="ee63a-115">XML</span><span class="sxs-lookup"><span data-stu-id="ee63a-115">XML</span></span>](index.md)

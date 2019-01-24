---
title: 'Nasıl yapılır: Erişim XML alt öğelerine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 92ecea2c2e6e117add37b30498f5fb34adfeac6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626665"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="d418a-102">Nasıl yapılır: Erişim XML alt öğelerine (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d418a-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="d418a-103">Bu örnek belirtilen ada sahip bir XML öğesi tüm XML alt öğelerine erişmek için axis özelliği bir alt kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d418a-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="d418a-104">Özellikle, kullandığı <xref:System.Xml.Linq.XElement.Value%2A> özelliğini koleksiyondaki ilk öğenin değerini alma `name` alt eksen özelliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d418a-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="d418a-105">`name` Child axis özelliği adlı tüm alt öğe alır `phone` içinde `contact` nesne.</span><span class="sxs-lookup"><span data-stu-id="d418a-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="d418a-106">Bu örnekte ayrıca `phone` adlı tüm alt öğelere erişmek için alt axis özelliği `phone` içerdiği `contact` nesne.</span><span class="sxs-lookup"><span data-stu-id="d418a-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d418a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d418a-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d418a-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d418a-108">Compiling the Code</span></span>  
 <span data-ttu-id="d418a-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d418a-109">This example requires:</span></span>  
  
-   <span data-ttu-id="d418a-110">Bir başvuru <xref:System.Xml.Linq> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d418a-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d418a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d418a-111">See also</span></span>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d418a-112">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="d418a-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="d418a-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="d418a-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="d418a-114">Visual Basic'de XML'e erişme</span><span class="sxs-lookup"><span data-stu-id="d418a-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="d418a-115">XML</span><span class="sxs-lookup"><span data-stu-id="d418a-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

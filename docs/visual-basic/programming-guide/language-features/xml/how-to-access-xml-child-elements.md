---
title: 'Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 4ec7743a30b8101d813ac414a8f5164aeb6c593d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649210"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="a2cc6-102">Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2cc6-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="a2cc6-103">Bu örnek belirtilen ada sahip bir XML öğesi tüm XML alt öğelerine erişmek için axis özelliği bir alt kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2cc6-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="a2cc6-104">Özellikle, kullanan <xref:System.Xml.Linq.XElement.Value%2A> özelliğine koleksiyonda ilk öğenin değerini almak `name` alt axis özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2cc6-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="a2cc6-105">`name` Child axis özelliği alır adlı tüm alt öğeleri `phone` içinde `contact` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a2cc6-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="a2cc6-106">Bu örnek ayrıca kullanır `phone` adlı tüm alt öğeleri erişmek için alt axis özelliği `phone` içerdiği `contact` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a2cc6-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2cc6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2cc6-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2cc6-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a2cc6-108">Compiling the Code</span></span>  
 <span data-ttu-id="a2cc6-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a2cc6-109">This example requires:</span></span>  
  
-   <span data-ttu-id="a2cc6-110">Bir başvuru <xref:System.Xml.Linq> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a2cc6-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2cc6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2cc6-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a2cc6-112">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="a2cc6-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="a2cc6-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="a2cc6-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="a2cc6-114">Visual Basic'de XML'e erişme</span><span class="sxs-lookup"><span data-stu-id="a2cc6-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="a2cc6-115">XML</span><span class="sxs-lookup"><span data-stu-id="a2cc6-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

---
title: 'Nasıl yapılır: Erişim XML alt öğelerine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: cd1b0db5305c7879d89cfdfff6cd458d6dea14f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836824"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="8acfe-102">Nasıl yapılır: Erişim XML alt öğelerine (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8acfe-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="8acfe-103">Bu örnek belirtilen ada sahip bir XML öğesi tüm XML alt öğelerine erişmek için axis özelliği bir alt kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8acfe-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="8acfe-104">Özellikle, kullandığı <xref:System.Xml.Linq.XElement.Value%2A> özelliğini koleksiyondaki ilk öğenin değerini alma `name` alt eksen özelliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8acfe-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="8acfe-105">`name` Child axis özelliği adlı tüm alt öğe alır `phone` içinde `contact` nesne.</span><span class="sxs-lookup"><span data-stu-id="8acfe-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="8acfe-106">Bu örnekte ayrıca `phone` adlı tüm alt öğelere erişmek için alt axis özelliği `phone` içerdiği `contact` nesne.</span><span class="sxs-lookup"><span data-stu-id="8acfe-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8acfe-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8acfe-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8acfe-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8acfe-108">Compiling the Code</span></span>  
 <span data-ttu-id="8acfe-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8acfe-109">This example requires:</span></span>  
  
-   <span data-ttu-id="8acfe-110">Bir başvuru <xref:System.Xml.Linq> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8acfe-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8acfe-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8acfe-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8acfe-112">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="8acfe-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="8acfe-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="8acfe-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="8acfe-114">Visual Basic'de XML'e erişme</span><span class="sxs-lookup"><span data-stu-id="8acfe-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="8acfe-115">XML</span><span class="sxs-lookup"><span data-stu-id="8acfe-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

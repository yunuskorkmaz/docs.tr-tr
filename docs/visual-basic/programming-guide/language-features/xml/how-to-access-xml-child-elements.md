---
title: 'Nasıl yapılır: XML Alt Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: af5ea809cb0777b16230f20e133764dd5f1f86d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332335"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="a7f48-102">Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7f48-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="a7f48-103">Bu örnek, bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7f48-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="a7f48-104">Özellikle, `name` alt eksen özelliğinin döndürdüğü koleksiyondaki ilk öğenin değerini almak için <xref:System.Xml.Linq.XElement.Value%2A> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7f48-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="a7f48-105">`name` alt eksen özelliği, `contact` nesnesinde `phone` adlı tüm alt öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="a7f48-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="a7f48-106">Bu örnek ayrıca `contact` nesnesinde bulunan `phone` adlı tüm alt öğelere erişmek için `phone` alt eksen özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7f48-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7f48-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7f48-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7f48-108">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="a7f48-108">Compiling the Code</span></span>  
 <span data-ttu-id="a7f48-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a7f48-109">This example requires:</span></span>  
  
- <span data-ttu-id="a7f48-110"><xref:System.Xml.Linq> ad alanına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="a7f48-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f48-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f48-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a7f48-112">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="a7f48-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="a7f48-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="a7f48-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="a7f48-114">Visual Basic XML 'e erişme</span><span class="sxs-lookup"><span data-stu-id="a7f48-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="a7f48-115">XML</span><span class="sxs-lookup"><span data-stu-id="a7f48-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

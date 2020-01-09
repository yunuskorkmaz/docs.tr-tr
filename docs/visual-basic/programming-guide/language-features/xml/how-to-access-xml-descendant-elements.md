---
title: 'Nasıl yapılır: XML Bağımlı Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347165"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="796e3-102">Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="796e3-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="796e3-103">Bu örnek, bir alt eksen özelliğinin, belirtilen bir ada sahip olan ve bir XML öğesi altında bulunan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="796e3-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="796e3-104">Özellikle, `name` alt eksen özelliğinin döndürdüğü koleksiyondaki ilk öğenin değerini almak için `Value` özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="796e3-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="796e3-105">`name` alt eksen özelliği, `contacts` nesnesinde bulunan `name` adlı tüm öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="796e3-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="796e3-106">Bu örnek ayrıca `contacts` nesnesinde bulunan `phone` adlı tüm alt öğelere erişmek için `phone` alt eksen özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="796e3-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="796e3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="796e3-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="796e3-108">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="796e3-108">Compile the code</span></span>  
 <span data-ttu-id="796e3-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="796e3-109">This example requires:</span></span>  
  
- <span data-ttu-id="796e3-110"><xref:System.Xml.Linq> ad alanına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="796e3-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796e3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="796e3-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="796e3-112">XML Descendant Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="796e3-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="796e3-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="796e3-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="796e3-114">Visual Basic XML 'e erişme</span><span class="sxs-lookup"><span data-stu-id="796e3-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="796e3-115">XML</span><span class="sxs-lookup"><span data-stu-id="796e3-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

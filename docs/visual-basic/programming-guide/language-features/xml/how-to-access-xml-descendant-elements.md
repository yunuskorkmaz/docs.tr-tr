---
title: 'Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 6d41844b540631df96740ce56818c125cf85e928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648492"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="c6ae2-102">Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6ae2-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="c6ae2-103">Bu örnek descendant axis özelliği, belirtilen ada sahip ve bir XML öğesi altında bulunan tüm XML öğeleri erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6ae2-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="c6ae2-104">Özellikle, kullanan `Value` özelliğine koleksiyonda ilk öğenin değerini almak `name` descendant axis özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6ae2-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="c6ae2-105">`name` Descendant axis özelliği alır adlı tüm öğeleri `name` içerdiği `contacts` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c6ae2-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="c6ae2-106">Bu örnek ayrıca kullanır `phone` adlı tüm bağımlı öğelerini erişmek için descendant axis özelliği `phone` içerdiği `contacts` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c6ae2-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6ae2-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6ae2-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6ae2-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c6ae2-108">Compiling the Code</span></span>  
 <span data-ttu-id="c6ae2-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c6ae2-109">This example requires:</span></span>  
  
-   <span data-ttu-id="c6ae2-110">Bir başvuru <xref:System.Xml.Linq> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c6ae2-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ae2-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6ae2-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="c6ae2-112">XML Descendant Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="c6ae2-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [<span data-ttu-id="c6ae2-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="c6ae2-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="c6ae2-114">Visual Basic'de XML'e erişme</span><span class="sxs-lookup"><span data-stu-id="c6ae2-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="c6ae2-115">XML</span><span class="sxs-lookup"><span data-stu-id="c6ae2-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

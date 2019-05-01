---
title: 'Nasıl yapılır: Erişim XML bağımlı öğelerine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: bfbf849bd296f639f03580346e4a9c52ce000abd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934816"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="cbb8e-102">Nasıl yapılır: Erişim XML bağımlı öğelerine (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbb8e-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="cbb8e-103">Bu örnek, bir descendant axis özelliği bir XML öğesi altında yer alır ve belirtilen ada sahip olan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbb8e-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="cbb8e-104">Özellikle, kullandığı `Value` özelliğini koleksiyondaki ilk öğenin değerini alma `name` descendant axis özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="cbb8e-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="cbb8e-105">`name` Descendant axis özelliği adlı tüm öğeleri alır `name` içerdiği `contacts` nesne.</span><span class="sxs-lookup"><span data-stu-id="cbb8e-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="cbb8e-106">Bu örnekte ayrıca `phone` adlı tüm alt öğeleri erişmeye descendant axis özelliği `phone` içerdiği `contacts` nesne.</span><span class="sxs-lookup"><span data-stu-id="cbb8e-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbb8e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="cbb8e-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cbb8e-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cbb8e-108">Compiling the Code</span></span>  
 <span data-ttu-id="cbb8e-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cbb8e-109">This example requires:</span></span>  
  
- <span data-ttu-id="cbb8e-110">Bir başvuru <xref:System.Xml.Linq> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cbb8e-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb8e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbb8e-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cbb8e-112">XML Descendant Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="cbb8e-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="cbb8e-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="cbb8e-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="cbb8e-114">Visual Basic'de XML'e erişme</span><span class="sxs-lookup"><span data-stu-id="cbb8e-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="cbb8e-115">XML</span><span class="sxs-lookup"><span data-stu-id="cbb8e-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

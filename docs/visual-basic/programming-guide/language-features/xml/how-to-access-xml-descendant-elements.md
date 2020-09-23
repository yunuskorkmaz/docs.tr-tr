---
title: 'Nasıl yapılır: XML Bağımlı Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: dcbaf1f9022d86f40a90ef6a1e0033f627caeef2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058215"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="bc392-102">Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc392-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>

<span data-ttu-id="bc392-103">Bu örnek, bir alt eksen özelliğinin, belirtilen bir ada sahip olan ve bir XML öğesi altında bulunan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc392-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="bc392-104">Özellikle, alt `Value` eksen özelliğinin döndürdüğü koleksiyondaki ilk öğenin değerini almak için özelliğini kullanır `name` .</span><span class="sxs-lookup"><span data-stu-id="bc392-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="bc392-105">Alt `name` eksen özelliği, nesnesinde bulunan adlı tüm öğeleri alır `name` `contacts` .</span><span class="sxs-lookup"><span data-stu-id="bc392-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="bc392-106">Bu örnek, `phone` nesnesinde bulunan adlı tüm alt öğelere erişmek için alt eksen özelliğini de kullanır `phone` `contacts` .</span><span class="sxs-lookup"><span data-stu-id="bc392-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc392-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc392-107">Example</span></span>  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="bc392-108">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="bc392-108">Compile the code</span></span>  

 <span data-ttu-id="bc392-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bc392-109">This example requires:</span></span>  
  
- <span data-ttu-id="bc392-110"><xref:System.Xml.Linq>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="bc392-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc392-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc392-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc392-112">XML Descendant Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="bc392-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="bc392-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="bc392-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="bc392-114">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="bc392-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="bc392-115">XML</span><span class="sxs-lookup"><span data-stu-id="bc392-115">XML</span></span>](index.md)

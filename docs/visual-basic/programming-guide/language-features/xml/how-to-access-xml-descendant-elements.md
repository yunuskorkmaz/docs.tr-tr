---
title: 'Nasıl yapılır: XML Bağımlı Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 03c403aa3c187b0b9d2006104eccaa1f9cd8aec5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392642"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="f2808-102">Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2808-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="f2808-103">Bu örnek, bir alt eksen özelliğinin, belirtilen bir ada sahip olan ve bir XML öğesi altında bulunan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2808-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="f2808-104">Özellikle, alt `Value` eksen özelliğinin döndürdüğü koleksiyondaki ilk öğenin değerini almak için özelliğini kullanır `name` .</span><span class="sxs-lookup"><span data-stu-id="f2808-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="f2808-105">Alt `name` eksen özelliği, nesnesinde bulunan adlı tüm öğeleri alır `name` `contacts` .</span><span class="sxs-lookup"><span data-stu-id="f2808-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="f2808-106">Bu örnek, `phone` nesnesinde bulunan adlı tüm alt öğelere erişmek için alt eksen özelliğini de kullanır `phone` `contacts` .</span><span class="sxs-lookup"><span data-stu-id="f2808-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2808-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2808-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="f2808-108">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="f2808-108">Compile the code</span></span>  
 <span data-ttu-id="f2808-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f2808-109">This example requires:</span></span>  
  
- <span data-ttu-id="f2808-110"><xref:System.Xml.Linq>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="f2808-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2808-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2808-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f2808-112">XML Descendant Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="f2808-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="f2808-113">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="f2808-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="f2808-114">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="f2808-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="f2808-115">XML</span><span class="sxs-lookup"><span data-stu-id="f2808-115">XML</span></span>](index.md)

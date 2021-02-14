---
description: 'Daha fazla bilgi edinin: nasıl yapılır: XML alt öğelerine erişme (Visual Basic)'
title: 'Nasıl yapılır: XML Bağımlı Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: d8f3176a91c2f637f49d2754513f3253399ee8ed
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433180"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="9a655-103">Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a655-103">How to: Access XML Descendant Elements (Visual Basic)</span></span>

<span data-ttu-id="9a655-104">Bu örnek, bir alt eksen özelliğinin, belirtilen bir ada sahip olan ve bir XML öğesi altında bulunan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a655-104">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="9a655-105">Özellikle, alt `Value` eksen özelliğinin döndürdüğü koleksiyondaki ilk öğenin değerini almak için özelliğini kullanır `name` .</span><span class="sxs-lookup"><span data-stu-id="9a655-105">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="9a655-106">Alt `name` eksen özelliği, nesnesinde bulunan adlı tüm öğeleri alır `name` `contacts` .</span><span class="sxs-lookup"><span data-stu-id="9a655-106">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="9a655-107">Bu örnek, `phone` nesnesinde bulunan adlı tüm alt öğelere erişmek için alt eksen özelliğini de kullanır `phone` `contacts` .</span><span class="sxs-lookup"><span data-stu-id="9a655-107">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a655-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a655-108">Example</span></span>  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="9a655-109">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="9a655-109">Compile the code</span></span>  

 <span data-ttu-id="9a655-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9a655-110">This example requires:</span></span>  
  
- <span data-ttu-id="9a655-111"><xref:System.Xml.Linq>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="9a655-111">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a655-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a655-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9a655-113">XML Descendant Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="9a655-113">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="9a655-114">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="9a655-114">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="9a655-115">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="9a655-115">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="9a655-116">XML</span><span class="sxs-lookup"><span data-stu-id="9a655-116">XML</span></span>](index.md)

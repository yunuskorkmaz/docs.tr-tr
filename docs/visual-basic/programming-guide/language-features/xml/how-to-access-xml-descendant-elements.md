---
title: "Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b3b6c8ac96bd18a379804b83f3ab3e48a5b0c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="00650-102">Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00650-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="00650-103">Bu örnek descendant axis özelliği, belirtilen ada sahip ve bir XML öğesi altında bulunan tüm XML öğeleri erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="00650-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="00650-104">Özellikle, kullanan `Value` özelliğine koleksiyonda ilk öğenin değerini almak `name` descendant axis özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="00650-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="00650-105">`name` Descendant axis özelliği alır adlı tüm öğeleri `name` içerdiği `contacts` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="00650-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="00650-106">Bu örnek ayrıca kullanır `phone` adlı tüm bağımlı öğelerini erişmek için descendant axis özelliği `phone` içerdiği `contacts` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="00650-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00650-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="00650-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00650-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="00650-108">Compiling the Code</span></span>  
 <span data-ttu-id="00650-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="00650-109">This example requires:</span></span>  
  
-   <span data-ttu-id="00650-110">Bir başvuru <xref:System.Xml.Linq> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="00650-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00650-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00650-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="00650-112">XML Descendant Axis özelliği</span><span class="sxs-lookup"><span data-stu-id="00650-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [<span data-ttu-id="00650-113">XML değeri özelliği</span><span class="sxs-lookup"><span data-stu-id="00650-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="00650-114">Visual Basic'de XML'e erişme</span><span class="sxs-lookup"><span data-stu-id="00650-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="00650-115">XML</span><span class="sxs-lookup"><span data-stu-id="00650-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

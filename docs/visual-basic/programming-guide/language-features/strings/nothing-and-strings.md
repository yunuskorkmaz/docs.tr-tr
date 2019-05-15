---
title: Visual Basic'de Dizeler ve Nothing
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: f5c1ea8cc0728b25e8e874963967aed504e466d7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591352"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="0dedd-102">Visual Basic'de Dizeler ve Nothing</span><span class="sxs-lookup"><span data-stu-id="0dedd-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="0dedd-103">Visual Basic çalışma zamanı ve .NET Framework'ü değerlendirmek `Nothing` farklı dizelere geldiğinde.</span><span class="sxs-lookup"><span data-stu-id="0dedd-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="0dedd-104">Visual Basic çalışma zamanı ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0dedd-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="0dedd-105">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0dedd-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="0dedd-106">Visual Basic çalışma zamanı genellikle değerlendirir `Nothing` olarak boş bir dize ("").</span><span class="sxs-lookup"><span data-stu-id="0dedd-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="0dedd-107">.NET Framework, ancak içermediği ve dize işlemi gerçekleştirmek için bir girişimde her bir özel durum oluşturur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="0dedd-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dedd-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dedd-108">See also</span></span>

- [<span data-ttu-id="0dedd-109">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="0dedd-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)

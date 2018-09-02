---
title: Visual Basic'de Dizeler ve Nothing
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425217"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="612a1-102">Visual Basic'de Dizeler ve Nothing</span><span class="sxs-lookup"><span data-stu-id="612a1-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="612a1-103">Visual Basic çalışma zamanı ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] değerlendirmek `Nothing` farklı dizelere geldiğinde.</span><span class="sxs-lookup"><span data-stu-id="612a1-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="612a1-104">Visual Basic çalışma zamanı ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="612a1-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="612a1-105">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="612a1-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="612a1-106">Visual Basic çalışma zamanı genellikle değerlendirir `Nothing` olarak boş bir dize ("").</span><span class="sxs-lookup"><span data-stu-id="612a1-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="612a1-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Dize işlemi gerçekleştirmek için bir girişimde her bir özel durum oluşturur ve ancak desteklemez, `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="612a1-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612a1-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="612a1-108">See Also</span></span>  
 [<span data-ttu-id="612a1-109">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="612a1-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)

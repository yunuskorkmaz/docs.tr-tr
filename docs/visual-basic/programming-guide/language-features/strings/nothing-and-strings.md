---
title: Visual Basic'de Dizeler ve Nothing
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 873c4e40a0b12dd657d3294785e04dd9efc23956
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967995"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="7f1d4-102">Visual Basic'de Dizeler ve Nothing</span><span class="sxs-lookup"><span data-stu-id="7f1d4-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="7f1d4-103">Visual Basic çalışma zamanı ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] değerlendirmek `Nothing` farklı dizelere geldiğinde.</span><span class="sxs-lookup"><span data-stu-id="7f1d4-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="7f1d4-104">Visual Basic çalışma zamanı ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7f1d4-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="7f1d4-105">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7f1d4-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="7f1d4-106">Visual Basic çalışma zamanı genellikle değerlendirir `Nothing` olarak boş bir dize ("").</span><span class="sxs-lookup"><span data-stu-id="7f1d4-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="7f1d4-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Dize işlemi gerçekleştirmek için bir girişimde her bir özel durum oluşturur ve ancak desteklemez, `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7f1d4-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f1d4-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f1d4-108">See also</span></span>
- [<span data-ttu-id="7f1d4-109">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="7f1d4-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)

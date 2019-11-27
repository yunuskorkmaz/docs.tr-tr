---
title: Nothing ve Dizeler
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: dfc43748d0754f0a6a29763c42ab82d9937f89f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344303"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="992ce-102">Visual Basic'de Dizeler ve Nothing</span><span class="sxs-lookup"><span data-stu-id="992ce-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="992ce-103">Visual Basic çalışma zamanı ve .NET Framework, dizelerde `Nothing` farklı şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="992ce-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="992ce-104">Çalışma zamanı ve .NET Framework Visual Basic</span><span class="sxs-lookup"><span data-stu-id="992ce-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="992ce-105">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="992ce-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="992ce-106">Visual Basic çalışma zamanı genellikle `Nothing` boş bir dize ("") olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="992ce-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="992ce-107">.NET Framework, ancak `Nothing`bir dize işlemi gerçekleştirmek için bir deneme yapıldığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="992ce-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992ce-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="992ce-108">See also</span></span>

- [<span data-ttu-id="992ce-109">Visual Basic dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="992ce-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)

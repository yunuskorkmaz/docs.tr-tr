---
title: Nothing ve Dizeler
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 392de45b0ee1688224f3e8170b0144f1acdb0912
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360572"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="a3068-102">Visual Basic'de Dizeler ve Nothing</span><span class="sxs-lookup"><span data-stu-id="a3068-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="a3068-103">Visual Basic çalışma zamanı ve .NET Framework, `Nothing` dizelere geldiğinde farklı şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a3068-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="a3068-104">Çalışma zamanı ve .NET Framework Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3068-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="a3068-105">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="a3068-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="a3068-106">Visual Basic çalışma zamanı genellikle `Nothing` boş bir dize ("") olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a3068-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="a3068-107">.NET Framework, ancak üzerinde bir dize işlemi gerçekleştirmek için bir girişimde bulunulduğunda bir özel durum oluşturur `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="a3068-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3068-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3068-108">See also</span></span>

- [<span data-ttu-id="a3068-109">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="a3068-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)

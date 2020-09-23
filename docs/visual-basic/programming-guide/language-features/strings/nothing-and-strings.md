---
title: Nothing ve Dizeler
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d4c7ee6d13334617a80abb845af52bf388a12797
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072528"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="bfe07-102">Visual Basic'de Dizeler ve Nothing</span><span class="sxs-lookup"><span data-stu-id="bfe07-102">Nothing and Strings in Visual Basic</span></span>

<span data-ttu-id="bfe07-103">Visual Basic çalışma zamanı ve .NET Framework, `Nothing` dizelere geldiğinde farklı şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bfe07-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="bfe07-104">Çalışma zamanı ve .NET Framework Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfe07-104">Visual Basic Runtime and the .NET Framework</span></span>  

 <span data-ttu-id="bfe07-105">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="bfe07-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="bfe07-106">Visual Basic çalışma zamanı genellikle `Nothing` boş bir dize ("") olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bfe07-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="bfe07-107">.NET Framework, ancak üzerinde bir dize işlemi gerçekleştirmek için bir girişimde bulunulduğunda bir özel durum oluşturur `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="bfe07-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe07-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfe07-108">See also</span></span>

- [<span data-ttu-id="bfe07-109">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="bfe07-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)

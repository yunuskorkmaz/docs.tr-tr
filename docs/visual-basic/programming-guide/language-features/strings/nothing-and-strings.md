---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic Nothing ve dizeler'
title: Nothing ve Dizeler
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: a32dd8b38033f1845f2ada87bf5f538d45fede18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424352"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="8f575-103">Visual Basic'de Dizeler ve Nothing</span><span class="sxs-lookup"><span data-stu-id="8f575-103">Nothing and Strings in Visual Basic</span></span>

<span data-ttu-id="8f575-104">Visual Basic çalışma zamanı ve .NET Framework, `Nothing` dizelere geldiğinde farklı şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8f575-104">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="8f575-105">Çalışma zamanı ve .NET Framework Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f575-105">Visual Basic Runtime and the .NET Framework</span></span>  

 <span data-ttu-id="8f575-106">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="8f575-106">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="8f575-107">Visual Basic çalışma zamanı genellikle `Nothing` boş bir dize ("") olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8f575-107">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="8f575-108">.NET Framework, ancak üzerinde bir dize işlemi gerçekleştirmek için bir girişimde bulunulduğunda bir özel durum oluşturur `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="8f575-108">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f575-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f575-109">See also</span></span>

- [<span data-ttu-id="8f575-110">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="8f575-110">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)

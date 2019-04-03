---
title: Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 85573099ec0a3f8a23c17bdf384c4c105f9157df
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825800"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="058d5-102">Deyim, bir satır 'If' deyimi dışında blok sona erdiremez</span><span class="sxs-lookup"><span data-stu-id="058d5-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="058d5-103">Tek satırlı `If` deyimi biri olan virgülle (:) ayırarak çeşitli deyimleri içeren bir `End` deyim için bir denetim bloğu tek satır dışında `If`.</span><span class="sxs-lookup"><span data-stu-id="058d5-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="058d5-104">Tek satırlı `If` deyimleri kullanmayın `End If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="058d5-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="058d5-105">**Hata Kimliği:** BC32005</span><span class="sxs-lookup"><span data-stu-id="058d5-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="058d5-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="058d5-106">To correct this error</span></span>  
  
-   <span data-ttu-id="058d5-107">Tek satırlı taşıma `If` içeren denetim bloğu dışında bir deyim `End If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="058d5-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="058d5-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="058d5-108">See also</span></span>

- [<span data-ttu-id="058d5-109">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="058d5-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

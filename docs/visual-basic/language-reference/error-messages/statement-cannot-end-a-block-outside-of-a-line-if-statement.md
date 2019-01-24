---
title: Deyim bir satır dışında blok sona &#39;varsa&#39; deyimi
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 78fe136acbd09e202b1daeb16dd540cf42ada390
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574722"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="2cda9-102">Deyim bir satır dışında blok sona &#39;varsa&#39; deyimi</span><span class="sxs-lookup"><span data-stu-id="2cda9-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="2cda9-103">Tek satırlı `If` deyimi biri olan virgülle (:) ayırarak çeşitli deyimleri içeren bir `End` deyim için bir denetim bloğu tek satır dışında `If`.</span><span class="sxs-lookup"><span data-stu-id="2cda9-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="2cda9-104">Tek satırlı `If` deyimleri kullanmayın `End If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2cda9-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="2cda9-105">**Hata Kimliği:** BC32005</span><span class="sxs-lookup"><span data-stu-id="2cda9-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2cda9-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2cda9-106">To correct this error</span></span>  
  
-   <span data-ttu-id="2cda9-107">Tek satırlı taşıma `If` içeren denetim bloğu dışında bir deyim `End If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2cda9-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cda9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cda9-108">See also</span></span>
- [<span data-ttu-id="2cda9-109">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="2cda9-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

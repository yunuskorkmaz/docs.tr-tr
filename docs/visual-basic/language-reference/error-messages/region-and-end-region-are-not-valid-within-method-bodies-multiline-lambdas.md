---
title: "'#Region' ve '#End Region' deyimleri yöntem gövdeleri / çok satırlı lambdalar içinde geçerli değildir."
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: deef3de645040d7c3d95b1a6c8a25fcf10de881b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842713"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="e1f15-102">'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="e1f15-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="e1f15-103">`#Region` Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1f15-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="e1f15-104">Daraltılabilir bir bölgeye bir veya daha fazla yordamlar içerebilir, ancak bunu başlayamaz veya bitemez bir yordam içinde.</span><span class="sxs-lookup"><span data-stu-id="e1f15-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="e1f15-105">**Hata Kimliği:** BC32025</span><span class="sxs-lookup"><span data-stu-id="e1f15-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1f15-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e1f15-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="e1f15-107">Yukarıdaki yordamı ile düzgün bir şekilde sonlandırıldığından emin olun bir `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e1f15-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="e1f15-108">Emin `#Region` ve `#End Region` yönergeleridir aynı kod bloğu.</span><span class="sxs-lookup"><span data-stu-id="e1f15-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f15-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1f15-109">See also</span></span>

- [<span data-ttu-id="e1f15-110">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="e1f15-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)

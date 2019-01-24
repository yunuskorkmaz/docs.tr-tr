---
title: '&#39;#Region&#39; ve &#39;#End Region&#39; deyimleri yöntem gövdeleri / çok satırlı lambdalar içinde geçerli değildir'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 55399cd123ce4d67cc833f2eabe3230acdafc0bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737221"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="fe53e-102">&#39;#Region&#39; ve &#39;#End Region&#39; deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="fe53e-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="fe53e-103">`#Region` Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe53e-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="fe53e-104">Daraltılabilir bir bölgeye bir veya daha fazla yordamlar içerebilir, ancak bunu başlayamaz veya bitemez bir yordam içinde.</span><span class="sxs-lookup"><span data-stu-id="fe53e-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="fe53e-105">**Hata Kimliği:** BC32025</span><span class="sxs-lookup"><span data-stu-id="fe53e-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fe53e-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fe53e-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="fe53e-107">Yukarıdaki yordamı ile düzgün bir şekilde sonlandırıldığından emin olun bir `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fe53e-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="fe53e-108">Emin `#Region` ve `#End Region` yönergeleridir aynı kod bloğu.</span><span class="sxs-lookup"><span data-stu-id="fe53e-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe53e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe53e-109">See also</span></span>
- [<span data-ttu-id="fe53e-110">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="fe53e-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)

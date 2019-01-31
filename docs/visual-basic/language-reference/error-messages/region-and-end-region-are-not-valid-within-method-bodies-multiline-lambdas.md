---
title: "'#Region' ve '#End Region' deyimleri yöntem gövdeleri / çok satırlı lambdalar içinde geçerli değildir."
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 2a2f5692518c6784dfc6e3be6302f1e8dcf2aaa7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265577"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="86a69-102">'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="86a69-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="86a69-103">`#Region` Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="86a69-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="86a69-104">Daraltılabilir bir bölgeye bir veya daha fazla yordamlar içerebilir, ancak bunu başlayamaz veya bitemez bir yordam içinde.</span><span class="sxs-lookup"><span data-stu-id="86a69-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="86a69-105">**Hata Kimliği:** BC32025</span><span class="sxs-lookup"><span data-stu-id="86a69-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="86a69-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="86a69-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="86a69-107">Yukarıdaki yordamı ile düzgün bir şekilde sonlandırıldığından emin olun bir `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="86a69-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="86a69-108">Emin `#Region` ve `#End Region` yönergeleridir aynı kod bloğu.</span><span class="sxs-lookup"><span data-stu-id="86a69-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a69-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86a69-109">See also</span></span>
- [<span data-ttu-id="86a69-110">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="86a69-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)

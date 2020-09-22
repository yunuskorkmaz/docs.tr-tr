---
title: "'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: e3147b6192f54ce85d0fecd6b67f7d80f6281b54
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870884"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="8e3e9-102">'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="8e3e9-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="8e3e9-103">`#Region`Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8e3e9-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="8e3e9-104">Daraltılabilir bir bölge bir veya daha fazla yordam içerebilir, ancak bir yordamın içinde başlayamaz veya bitemez.</span><span class="sxs-lookup"><span data-stu-id="8e3e9-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="8e3e9-105">**Hata kimliği:** BC32025</span><span class="sxs-lookup"><span data-stu-id="8e3e9-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e3e9-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8e3e9-106">To correct this error</span></span>  
  
1. <span data-ttu-id="8e3e9-107">Önceki yordamın bir veya ifadesiyle doğru şekilde sonlandırıldığı emin `End Function` olun `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="8e3e9-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="8e3e9-108">`#Region`Ve `#End Region` yönergelerinin aynı kod bloğunda bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8e3e9-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3e9-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e3e9-109">See also</span></span>

- [<span data-ttu-id="8e3e9-110">#Region yönergesi</span><span class="sxs-lookup"><span data-stu-id="8e3e9-110">#Region Directive</span></span>](../directives/region-directive.md)

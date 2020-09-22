---
title: "'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 91e6c81bb64c259411cbef8a36629b8b320ea584
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873762"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="69db5-102">'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="69db5-102">'Module' statements can occur only at file or namespace level</span></span>

<span data-ttu-id="69db5-103">`Module` deyimler, kaynak dosyanızın en üstünde `Option` ve `Imports` deyimleri, genel öznitelikleri ve ad alanı bildirimlerinden önce, diğer tüm bildirimlerden önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="69db5-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="69db5-104">**Hata kimliği:** BC30617</span><span class="sxs-lookup"><span data-stu-id="69db5-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69db5-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="69db5-105">To correct this error</span></span>  
  
- <span data-ttu-id="69db5-106">`Module`İfadeyi ad alanı bildiriminin veya kaynak dosyanın en üstüne taşıyın.</span><span class="sxs-lookup"><span data-stu-id="69db5-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69db5-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69db5-107">See also</span></span>

- [<span data-ttu-id="69db5-108">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="69db5-108">Module Statement</span></span>](../statements/module-statement.md)

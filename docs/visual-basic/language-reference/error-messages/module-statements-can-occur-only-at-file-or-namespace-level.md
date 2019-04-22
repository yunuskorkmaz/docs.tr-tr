---
title: "'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bf0239422fb5a98e4670aea407f684753d3a7ea4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825449"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="c328d-102">'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="c328d-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="c328d-103">`Module` deyimleri, kaynak dosyasının en üstüne görünmelidir hemen sonra `Option` ve `Imports` deyimleri, genel öznitelik ve ad alanı bildirimi, ancak önce diğer tüm bildirimler.</span><span class="sxs-lookup"><span data-stu-id="c328d-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="c328d-104">**Hata Kimliği:** BC30617</span><span class="sxs-lookup"><span data-stu-id="c328d-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c328d-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c328d-105">To correct this error</span></span>  
  
-   <span data-ttu-id="c328d-106">Taşıma `Module` ad alanı bildirimi veya kaynak dosyasının en üstüne deyimi.</span><span class="sxs-lookup"><span data-stu-id="c328d-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c328d-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c328d-107">See also</span></span>

- [<span data-ttu-id="c328d-108">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="c328d-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

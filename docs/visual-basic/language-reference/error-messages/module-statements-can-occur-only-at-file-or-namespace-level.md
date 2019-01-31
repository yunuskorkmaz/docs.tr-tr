---
title: "'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 0820763cce9cc27f9a379ed5e766e0691a75f36b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271271"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="b0362-102">'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="b0362-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="b0362-103">`Module` deyimleri, kaynak dosyasının en üstüne görünmelidir hemen sonra `Option` ve `Imports` deyimleri, genel öznitelik ve ad alanı bildirimi, ancak önce diğer tüm bildirimler.</span><span class="sxs-lookup"><span data-stu-id="b0362-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="b0362-104">**Hata Kimliği:** BC30617</span><span class="sxs-lookup"><span data-stu-id="b0362-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0362-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b0362-105">To correct this error</span></span>  
  
-   <span data-ttu-id="b0362-106">Taşıma `Module` ad alanı bildirimi veya kaynak dosyasının en üstüne deyimi.</span><span class="sxs-lookup"><span data-stu-id="b0362-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0362-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0362-107">See also</span></span>
- [<span data-ttu-id="b0362-108">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0362-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

---
title: '&#39;Modül&#39; deyimleri yalnızca dosya veya ad alanı düzeyinde oluşabilir'
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bdbf8df5942e9df4b9696aeea4e3492121efe21a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746318"
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="aa964-102">&#39;Modül&#39; deyimleri yalnızca dosya veya ad alanı düzeyinde oluşabilir</span><span class="sxs-lookup"><span data-stu-id="aa964-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="aa964-103">`Module` deyimleri, kaynak dosyasının en üstüne görünmelidir hemen sonra `Option` ve `Imports` deyimleri, genel öznitelik ve ad alanı bildirimi, ancak önce diğer tüm bildirimler.</span><span class="sxs-lookup"><span data-stu-id="aa964-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="aa964-104">**Hata Kimliği:** BC30617</span><span class="sxs-lookup"><span data-stu-id="aa964-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa964-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="aa964-105">To correct this error</span></span>  
  
-   <span data-ttu-id="aa964-106">Taşıma `Module` ad alanı bildirimi veya kaynak dosyasının en üstüne deyimi.</span><span class="sxs-lookup"><span data-stu-id="aa964-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa964-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa964-107">See also</span></span>
- [<span data-ttu-id="aa964-108">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="aa964-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

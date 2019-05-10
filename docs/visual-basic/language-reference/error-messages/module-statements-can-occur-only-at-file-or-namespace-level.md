---
title: "'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: fc3c102dbfe7c55e66093421bc11379d48ba000d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592093"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="ea85f-102">'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="ea85f-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="ea85f-103">`Module` deyimleri, kaynak dosyasının en üstüne görünmelidir hemen sonra `Option` ve `Imports` deyimleri, genel öznitelik ve ad alanı bildirimi, ancak önce diğer tüm bildirimler.</span><span class="sxs-lookup"><span data-stu-id="ea85f-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="ea85f-104">**Hata Kimliği:** BC30617</span><span class="sxs-lookup"><span data-stu-id="ea85f-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ea85f-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ea85f-105">To correct this error</span></span>  
  
- <span data-ttu-id="ea85f-106">Taşıma `Module` ad alanı bildirimi veya kaynak dosyasının en üstüne deyimi.</span><span class="sxs-lookup"><span data-stu-id="ea85f-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea85f-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea85f-107">See also</span></span>

- [<span data-ttu-id="ea85f-108">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="ea85f-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

---
title: '&#39;Sınıf&#39; deyimi, eşleşen bir ile bitmelidir &#39;son sınıfı&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 7c9051b15f6d9cf37d7d0245f758905467d5bbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585521"
---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a><span data-ttu-id="bc8c9-102">&#39;Sınıf&#39; deyimi, eşleşen bir ile bitmelidir &#39;son sınıfı&#39;</span><span class="sxs-lookup"><span data-stu-id="bc8c9-102">&#39;Class&#39; statement must end with a matching &#39;End Class&#39;</span></span>
<span data-ttu-id="bc8c9-103">`Class` başlatmak için kullanılan bir `Class` engelle; Bu nedenle, yalnızca eşleşen bloğun başlangıcında görünebilir `End Class` blok bitiş bildirimi.</span><span class="sxs-lookup"><span data-stu-id="bc8c9-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="bc8c9-104">Ya da bir yedek sahip `Class` deyimi veya olmayan sona erdi, `Class` ile engelleme `End Class`.</span><span class="sxs-lookup"><span data-stu-id="bc8c9-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="bc8c9-105">**Hata Kimliği:** BC30481</span><span class="sxs-lookup"><span data-stu-id="bc8c9-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc8c9-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bc8c9-106">To correct this error</span></span>  
  
-   <span data-ttu-id="bc8c9-107">Bulun ve gereksiz kaldırmak `Class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="bc8c9-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="bc8c9-108">Sonlandırma `Class` ile eşleşen bir blok `End Class`.</span><span class="sxs-lookup"><span data-stu-id="bc8c9-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8c9-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc8c9-109">See Also</span></span>  
 [<span data-ttu-id="bc8c9-110">Son \<anahtar sözcüğü > deyimi</span><span class="sxs-lookup"><span data-stu-id="bc8c9-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)  
 [<span data-ttu-id="bc8c9-111">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="bc8c9-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

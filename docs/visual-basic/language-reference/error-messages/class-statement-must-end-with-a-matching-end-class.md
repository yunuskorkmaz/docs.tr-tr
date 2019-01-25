---
title: '&#39;Sınıf&#39; deyimi, eşleşen ile bitmelidir &#39;son sınıfı&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 4e80ce58048bfa7f2fecc65e7167479df07bf57c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715094"
---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a><span data-ttu-id="d42cb-102">&#39;Sınıf&#39; deyimi, eşleşen ile bitmelidir &#39;son sınıfı&#39;</span><span class="sxs-lookup"><span data-stu-id="d42cb-102">&#39;Class&#39; statement must end with a matching &#39;End Class&#39;</span></span>
<span data-ttu-id="d42cb-103">`Class` başlatmak için kullanılan bir `Class` engelle; Bu nedenle yalnızca eşleşen bloğu başında görünebilir `End Class` blok sonlandırma deyimi.</span><span class="sxs-lookup"><span data-stu-id="d42cb-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="d42cb-104">Ya da bir yedek sahip `Class` deyimi veya değil sona erdi, `Class` ile block `End Class`.</span><span class="sxs-lookup"><span data-stu-id="d42cb-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="d42cb-105">**Hata Kimliği:** BC30481</span><span class="sxs-lookup"><span data-stu-id="d42cb-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d42cb-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d42cb-106">To correct this error</span></span>  
  
-   <span data-ttu-id="d42cb-107">Bulmak ve gereksiz kaldırma `Class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d42cb-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="d42cb-108">Sonlandırma `Class` ile eşleşen bir blok `End Class`.</span><span class="sxs-lookup"><span data-stu-id="d42cb-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d42cb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d42cb-109">See also</span></span>
- [<span data-ttu-id="d42cb-110">Son \<anahtar sözcüğü > deyimi</span><span class="sxs-lookup"><span data-stu-id="d42cb-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [<span data-ttu-id="d42cb-111">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="d42cb-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

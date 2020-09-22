---
title: "'Class' deyimi eşleşen bir 'End Class' ile bitmelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: d67f0e71dbdbf97420ec5b5ba4b6f06acfba1bd9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874619"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="36019-102">'Class' deyimi eşleşen bir 'End Class' ile bitmelidir</span><span class="sxs-lookup"><span data-stu-id="36019-102">'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="36019-103">`Class` bir bloğu başlatmak için kullanılır `Class` ; Bu nedenle, bloğu sonlandıran eşleşen bir deyimle birlikte yalnızca bloğun başlangıcında görünebilirler `End Class` .</span><span class="sxs-lookup"><span data-stu-id="36019-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="36019-104">Bir yedekli `Class` deyiminiz var veya kendi bloğundan sonlandırılamıyor `Class` `End Class` .</span><span class="sxs-lookup"><span data-stu-id="36019-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="36019-105">**Hata kimliği:** BC30481</span><span class="sxs-lookup"><span data-stu-id="36019-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="36019-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="36019-106">To correct this error</span></span>  
  
- <span data-ttu-id="36019-107">Gereksiz deyimin yerini bulun ve kaldırın `Class` .</span><span class="sxs-lookup"><span data-stu-id="36019-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="36019-108">`Class`Bloğu eşleştirme ile sonuçlandırma `End Class` .</span><span class="sxs-lookup"><span data-stu-id="36019-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36019-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36019-109">See also</span></span>

- [<span data-ttu-id="36019-110">End \<keyword> ekstresi</span><span class="sxs-lookup"><span data-stu-id="36019-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="36019-111">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="36019-111">Class Statement</span></span>](../statements/class-statement.md)

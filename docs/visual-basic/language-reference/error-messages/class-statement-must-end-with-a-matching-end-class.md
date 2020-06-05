---
title: "'Class' deyimi eşleşen bir 'End Class' ile bitmelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 01c231f577d21028e9ef92f37c7ac5f7f1fe2aa3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415394"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="d2e35-102">'Class' deyimi eşleşen bir 'End Class' ile bitmelidir</span><span class="sxs-lookup"><span data-stu-id="d2e35-102">'Class' statement must end with a matching 'End Class'</span></span>
<span data-ttu-id="d2e35-103">`Class`bir bloğu başlatmak için kullanılır `Class` ; Bu nedenle, bloğu sonlandıran eşleşen bir deyimle birlikte yalnızca bloğun başlangıcında görünebilirler `End Class` .</span><span class="sxs-lookup"><span data-stu-id="d2e35-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="d2e35-104">Bir yedekli `Class` deyiminiz var veya kendi bloğundan sonlandırılamıyor `Class` `End Class` .</span><span class="sxs-lookup"><span data-stu-id="d2e35-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="d2e35-105">**Hata kimliği:** BC30481</span><span class="sxs-lookup"><span data-stu-id="d2e35-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2e35-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d2e35-106">To correct this error</span></span>  
  
- <span data-ttu-id="d2e35-107">Gereksiz deyimin yerini bulun ve kaldırın `Class` .</span><span class="sxs-lookup"><span data-stu-id="d2e35-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="d2e35-108">`Class`Bloğu eşleştirme ile sonuçlandırma `End Class` .</span><span class="sxs-lookup"><span data-stu-id="d2e35-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e35-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2e35-109">See also</span></span>

- [<span data-ttu-id="d2e35-110">End \<keyword> ekstresi</span><span class="sxs-lookup"><span data-stu-id="d2e35-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="d2e35-111">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="d2e35-111">Class Statement</span></span>](../statements/class-statement.md)

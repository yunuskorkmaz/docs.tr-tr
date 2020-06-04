---
title: "'<keyword>' yalnızca bir örnek yöntemi içinde geçerlidir"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 537689405ea30bdd7c075320eba58a8723a93cdb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397408"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="fefd8-102">'\<keyword>' yalnızca bir örnek yöntemi içinde geçerlidir</span><span class="sxs-lookup"><span data-stu-id="fefd8-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="fefd8-103">`Me`, `MyClass` Ve `MyBase` anahtar sözcükleri belirli sınıf örneklerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="fefd8-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="fefd8-104">Onları paylaşılan bir veya yordam içinde kullanamazsınız `Function` `Sub` .</span><span class="sxs-lookup"><span data-stu-id="fefd8-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="fefd8-105">**Hata kimliği:** BC30043</span><span class="sxs-lookup"><span data-stu-id="fefd8-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fefd8-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fefd8-106">To correct this error</span></span>  
  
- <span data-ttu-id="fefd8-107">Yordamından anahtar sözcüğünü kaldırın veya `Shared` yordam bildiriminden anahtar sözcüğü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fefd8-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefd8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fefd8-108">See also</span></span>

- [<span data-ttu-id="fefd8-109">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="fefd8-109">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="fefd8-110">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="fefd8-110">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="fefd8-111">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="fefd8-111">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)

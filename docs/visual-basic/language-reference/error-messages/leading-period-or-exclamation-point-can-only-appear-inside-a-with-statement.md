---
title: Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 149acc2baac0f45fa971a11f254d694526d140d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397330"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="ab50c-102">Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="ab50c-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="ab50c-103">Bir blok içinde olmayan bir nokta (.) veya ünlem işareti (!) `With` sol tarafta bir ifade olmadan meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="ab50c-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="ab50c-104">Üye erişimi ( `.` ) ve sözlük üye erişimi ( `!` ), üyeyi içeren öğeyi belirten bir ifade gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ab50c-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="ab50c-105">Bu, erişimcinin hemen solunda veya `With` üye erişimini içeren bir bloğun hedefi olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ab50c-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="ab50c-106">**Hata kimliği:** BC30157</span><span class="sxs-lookup"><span data-stu-id="ab50c-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab50c-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ab50c-107">To correct this error</span></span>  
  
1. <span data-ttu-id="ab50c-108">`With`Bloğun doğru biçimlendirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ab50c-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2. <span data-ttu-id="ab50c-109">`With`Blok yoksa, üyeyi içeren tanımlanmış bir öğe için değerlendirilen erişimcinin soluna bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ab50c-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab50c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab50c-110">See also</span></span>

- [<span data-ttu-id="ab50c-111">Koddaki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="ab50c-111">Special Characters in Code</span></span>](../../programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="ab50c-112">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab50c-112">With...End With Statement</span></span>](../statements/with-end-with-statement.md)

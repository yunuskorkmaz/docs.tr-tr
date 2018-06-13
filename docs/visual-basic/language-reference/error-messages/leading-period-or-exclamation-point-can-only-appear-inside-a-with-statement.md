---
title: Önde gelen &#39;. &#39; veya &#39;! &#39; yalnızca içinde görünebilir bir &#39;ile&#39; deyimi
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 7802b8e0aaf3dff83d5bfbe11f0b8bb1b5bb46cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589453"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a><span data-ttu-id="4e285-102">Önde gelen &#39;. &#39; veya &#39;! &#39; yalnızca içinde görünebilir bir &#39;ile&#39; deyimi</span><span class="sxs-lookup"><span data-stu-id="4e285-102">Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement</span></span>
<span data-ttu-id="4e285-103">Bir nokta (.) veya ünlem işareti (!) olmayan iç bir `With` soldaki bir ifade olmadan blok oluşur.</span><span class="sxs-lookup"><span data-stu-id="4e285-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="4e285-104">Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üyeyi içeren öğe belirten bir ifade gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4e285-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="4e285-105">Bu hemen solundaki erişimci veya hedefi olarak görünmelidir bir `With` üye erişimi içeren bloğu.</span><span class="sxs-lookup"><span data-stu-id="4e285-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="4e285-106">**Hata Kimliği:** BC30157</span><span class="sxs-lookup"><span data-stu-id="4e285-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4e285-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4e285-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="4e285-108">Emin `With` blok doğru biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="4e285-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="4e285-109">Varsa hiçbir `With` engellemek, bir ifade değerlendirir erişimci üyeyi içeren tanımlanmış bir öğe sola ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4e285-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e285-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e285-110">See Also</span></span>  
 [<span data-ttu-id="4e285-111">Code'daki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="4e285-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [<span data-ttu-id="4e285-112">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="4e285-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

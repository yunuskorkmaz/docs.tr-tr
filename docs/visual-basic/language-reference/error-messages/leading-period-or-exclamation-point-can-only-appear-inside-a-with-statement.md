---
title: Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 15390fb506fe9bca10f6917f5b26451a5569bece
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921127"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="1c6ce-102">Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="1c6ce-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="1c6ce-103">Bir nokta (.) ya da ünlem işareti (!) olmayan iç bir `With` olmadan bir ifade soldaki blok gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1c6ce-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="1c6ce-104">Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üye içeren öğeyi belirten bir ifade gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1c6ce-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="1c6ce-105">Bu hemen erişimcisinin veya hedefi olarak sola görünmelidir bir `With` üye erişimi içeren yapı taşıdır.</span><span class="sxs-lookup"><span data-stu-id="1c6ce-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="1c6ce-106">**Hata Kimliği:** BC30157</span><span class="sxs-lookup"><span data-stu-id="1c6ce-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c6ce-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1c6ce-107">To correct this error</span></span>  
  
1. <span data-ttu-id="1c6ce-108">Emin `With` blok hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="1c6ce-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2. <span data-ttu-id="1c6ce-109">Yoksa hiçbir `With` engelleme, değerlendirilen erişimcisinin üyeyi içeren tanımlanmış bir öğe sola bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c6ce-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c6ce-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c6ce-110">See also</span></span>

- [<span data-ttu-id="1c6ce-111">Code'daki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="1c6ce-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="1c6ce-112">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="1c6ce-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

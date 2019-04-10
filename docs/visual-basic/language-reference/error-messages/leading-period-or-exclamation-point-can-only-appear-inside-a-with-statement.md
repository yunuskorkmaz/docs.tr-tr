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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322855"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="0abca-102">Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="0abca-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="0abca-103">Bir nokta (.) ya da ünlem işareti (!) olmayan iç bir `With` olmadan bir ifade soldaki blok gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="0abca-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="0abca-104">Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üye içeren öğeyi belirten bir ifade gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0abca-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="0abca-105">Bu hemen erişimcisinin veya hedefi olarak sola görünmelidir bir `With` üye erişimi içeren yapı taşıdır.</span><span class="sxs-lookup"><span data-stu-id="0abca-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="0abca-106">**Hata Kimliği:** BC30157</span><span class="sxs-lookup"><span data-stu-id="0abca-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0abca-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0abca-107">To correct this error</span></span>  
  
1. <span data-ttu-id="0abca-108">Emin `With` blok hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="0abca-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2. <span data-ttu-id="0abca-109">Yoksa hiçbir `With` engelleme, değerlendirilen erişimcisinin üyeyi içeren tanımlanmış bir öğe sola bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0abca-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abca-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0abca-110">See also</span></span>

- [<span data-ttu-id="0abca-111">Kod'da Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="0abca-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="0abca-112">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="0abca-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

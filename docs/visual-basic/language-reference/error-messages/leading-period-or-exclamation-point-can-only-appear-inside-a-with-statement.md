---
title: Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 367da8e7c9fd8c14a16a09b1f023e7637d78309d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259563"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="7d120-102">Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="7d120-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="7d120-103">Bir nokta (.) ya da ünlem işareti (!) olmayan iç bir `With` olmadan bir ifade soldaki blok gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7d120-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="7d120-104">Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üye içeren öğeyi belirten bir ifade gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d120-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="7d120-105">Bu hemen erişimcisinin veya hedefi olarak sola görünmelidir bir `With` üye erişimi içeren yapı taşıdır.</span><span class="sxs-lookup"><span data-stu-id="7d120-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="7d120-106">**Hata Kimliği:** BC30157</span><span class="sxs-lookup"><span data-stu-id="7d120-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7d120-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7d120-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="7d120-108">Emin `With` blok hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="7d120-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="7d120-109">Yoksa hiçbir `With` engelleme, değerlendirilen erişimcisinin üyeyi içeren tanımlanmış bir öğe sola bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7d120-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d120-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d120-110">See also</span></span>
- [<span data-ttu-id="7d120-111">Code'daki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="7d120-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="7d120-112">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="7d120-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

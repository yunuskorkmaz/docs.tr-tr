---
title: "Önde gelen &#39;. &#39; ya &#39;! &#39; içinde yalnızca görünebilir bir &#39; İle &#39; deyimi"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords: BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a><span data-ttu-id="5c89d-102">Önde gelen &#39;. &#39; ya &#39;! &#39; içinde yalnızca görünebilir bir &#39; İle &#39; deyimi</span><span class="sxs-lookup"><span data-stu-id="5c89d-102">Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement</span></span>
<span data-ttu-id="5c89d-103">Bir nokta (.) veya ünlem işareti (!) olmayan iç bir `With` soldaki bir ifade olmadan blok oluşur.</span><span class="sxs-lookup"><span data-stu-id="5c89d-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="5c89d-104">Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üyeyi içeren öğe belirten bir ifade gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5c89d-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="5c89d-105">Bu hemen solundaki erişimci veya hedefi olarak görünmelidir bir `With` üye erişimi içeren bloğu.</span><span class="sxs-lookup"><span data-stu-id="5c89d-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="5c89d-106">**Hata Kimliği:** BC30157</span><span class="sxs-lookup"><span data-stu-id="5c89d-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c89d-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5c89d-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="5c89d-108">Emin `With` blok doğru biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="5c89d-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="5c89d-109">Varsa hiçbir `With` engellemek, bir ifade değerlendirir erişimci üyeyi içeren tanımlanmış bir öğe sola ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5c89d-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c89d-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c89d-110">See Also</span></span>  
 [<span data-ttu-id="5c89d-111">Kod'da özel karakterler</span><span class="sxs-lookup"><span data-stu-id="5c89d-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [<span data-ttu-id="5c89d-112">İle... End With deyimi</span><span class="sxs-lookup"><span data-stu-id="5c89d-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

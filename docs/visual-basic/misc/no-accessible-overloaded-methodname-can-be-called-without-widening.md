---
title: "<methodname>Genişleyen dönüştürme olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz: <list>"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall_WideningConversion2
ms.assetid: 5e74f5cf-80bd-4b48-b58a-465f981ec694
ms.openlocfilehash: ed28e6c2f8336ff47bfae4021038f71bc7693c97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376605"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-widening-conversion-list"></a><span data-ttu-id="b3846-102">\<methodname>Genişleyen dönüştürme olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz:\<list></span><span class="sxs-lookup"><span data-stu-id="b3846-102">No accessible overloaded '\<methodname>' can be called with these arguments without a widening conversion: \<list></span></span>
<span data-ttu-id="b3846-103">Aşırı yüklenmiş bir yöntem çağrıldı, ancak Genişletme dönüştürmesi olmadan belirtilen bağımsız değişkenlerin listesiyle hiçbir yöntem eşleştiriyordu.</span><span class="sxs-lookup"><span data-stu-id="b3846-103">An overloaded method was called, but no method could be matched with the list of provided arguments without a widening conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3846-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b3846-104">To correct this error</span></span>  
  
- <span data-ttu-id="b3846-105">`Option Strict Off` belirtin.</span><span class="sxs-lookup"><span data-stu-id="b3846-105">Specify `Option Strict Off`.</span></span>  
  
- <span data-ttu-id="b3846-106">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzalarından biriyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b3846-106">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3846-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3846-107">See also</span></span>

- [<span data-ttu-id="b3846-108">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b3846-108">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="b3846-109">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="b3846-109">Option Strict Statement</span></span>](../language-reference/statements/option-strict-statement.md)

---
title: "<methodname>Genişleyen dönüştürme olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz: <list>"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall_WideningConversion2
ms.assetid: 5e74f5cf-80bd-4b48-b58a-465f981ec694
ms.openlocfilehash: cd4e53a7e7add983eefbf9c7176ebd7841e00563
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078911"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-widening-conversion-list"></a><span data-ttu-id="4350e-102">\<methodname>Genişleyen dönüştürme olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz:\<list></span><span class="sxs-lookup"><span data-stu-id="4350e-102">No accessible overloaded '\<methodname>' can be called with these arguments without a widening conversion: \<list></span></span>

<span data-ttu-id="4350e-103">Aşırı yüklenmiş bir yöntem çağrıldı, ancak Genişletme dönüştürmesi olmadan belirtilen bağımsız değişkenlerin listesiyle hiçbir yöntem eşleştiriyordu.</span><span class="sxs-lookup"><span data-stu-id="4350e-103">An overloaded method was called, but no method could be matched with the list of provided arguments without a widening conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4350e-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4350e-104">To correct this error</span></span>  
  
- <span data-ttu-id="4350e-105">`Option Strict Off` belirtin.</span><span class="sxs-lookup"><span data-stu-id="4350e-105">Specify `Option Strict Off`.</span></span>  
  
- <span data-ttu-id="4350e-106">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzalarından biriyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4350e-106">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4350e-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4350e-107">See also</span></span>

- [<span data-ttu-id="4350e-108">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="4350e-108">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="4350e-109">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="4350e-109">Option Strict Statement</span></span>](../language-reference/statements/option-strict-statement.md)

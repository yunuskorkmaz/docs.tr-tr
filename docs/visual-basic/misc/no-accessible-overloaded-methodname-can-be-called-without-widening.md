---
description: "Daha fazla bilgi edinin: hiçbir erişilebilir aşırı yüklenmiş ' <methodname> ', bu bağımsız değişkenlerle bir genişletme dönüştürmesi olmadan çağrılamaz: <list>"
title: "<methodname>Genişleyen dönüştürme olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz: <list>"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall_WideningConversion2
ms.assetid: 5e74f5cf-80bd-4b48-b58a-465f981ec694
ms.openlocfilehash: 68e3ecf16aac19ef644b0060b49b2b316f72e22e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479171"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-widening-conversion-list"></a><span data-ttu-id="fc2d1-103">\<methodname>Genişleyen dönüştürme olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz:\<list></span><span class="sxs-lookup"><span data-stu-id="fc2d1-103">No accessible overloaded '\<methodname>' can be called with these arguments without a widening conversion: \<list></span></span>

<span data-ttu-id="fc2d1-104">Aşırı yüklenmiş bir yöntem çağrıldı, ancak Genişletme dönüştürmesi olmadan belirtilen bağımsız değişkenlerin listesiyle hiçbir yöntem eşleştiriyordu.</span><span class="sxs-lookup"><span data-stu-id="fc2d1-104">An overloaded method was called, but no method could be matched with the list of provided arguments without a widening conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fc2d1-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fc2d1-105">To correct this error</span></span>  
  
- <span data-ttu-id="fc2d1-106">`Option Strict Off` belirtin.</span><span class="sxs-lookup"><span data-stu-id="fc2d1-106">Specify `Option Strict Off`.</span></span>  
  
- <span data-ttu-id="fc2d1-107">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzalarından biriyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc2d1-107">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2d1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc2d1-108">See also</span></span>

- [<span data-ttu-id="fc2d1-109">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="fc2d1-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="fc2d1-110">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="fc2d1-110">Option Strict Statement</span></span>](../language-reference/statements/option-strict-statement.md)

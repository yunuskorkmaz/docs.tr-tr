---
description: "Daha fazla bilgi edinin: <methodname> bir daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz: <list>"
title: "<methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz: <list>"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: a802b420a01c1894feca2c61c0bfdbb7be5104f5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475714"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a><span data-ttu-id="9390f-103">\<methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz:\<list></span><span class="sxs-lookup"><span data-stu-id="9390f-103">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion: \<list></span></span>

<span data-ttu-id="9390f-104">Aşırı yüklenmiş bir yöntem çağrıldı, ancak metot bir daraltma dönüştürmesi olmadan belirtilen bağımsız değişkenlerin listesiyle eşleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="9390f-104">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9390f-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9390f-105">To correct this error</span></span>  
  
1. <span data-ttu-id="9390f-106">`Option Strict Off` belirtin.</span><span class="sxs-lookup"><span data-stu-id="9390f-106">Specify `Option Strict Off`.</span></span>
  
2. <span data-ttu-id="9390f-107">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzasıyla eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9390f-107">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9390f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9390f-108">See also</span></span>

- [<span data-ttu-id="9390f-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9390f-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="9390f-110">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="9390f-110">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

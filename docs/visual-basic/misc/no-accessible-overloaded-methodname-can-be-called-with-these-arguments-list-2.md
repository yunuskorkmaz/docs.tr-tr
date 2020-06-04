---
title: "<methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz: <list>"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: f824b1250c7cb98aeaf301ef57ee01ec2779215f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376709"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a><span data-ttu-id="f8c37-102">\<methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz:\<list></span><span class="sxs-lookup"><span data-stu-id="f8c37-102">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion: \<list></span></span>
<span data-ttu-id="f8c37-103">Aşırı yüklenmiş bir yöntem çağrıldı, ancak metot bir daraltma dönüştürmesi olmadan belirtilen bağımsız değişkenlerin listesiyle eşleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="f8c37-103">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f8c37-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f8c37-104">To correct this error</span></span>  
  
1. <span data-ttu-id="f8c37-105">`Option Strict Off` belirtin.</span><span class="sxs-lookup"><span data-stu-id="f8c37-105">Specify `Option Strict Off`.</span></span>
  
2. <span data-ttu-id="f8c37-106">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzasıyla eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8c37-106">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c37-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8c37-107">See also</span></span>

- [<span data-ttu-id="f8c37-108">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="f8c37-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="f8c37-109">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="f8c37-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

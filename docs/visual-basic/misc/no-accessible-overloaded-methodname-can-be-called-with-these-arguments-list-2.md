---
title: "<methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz: <list>"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: 0c39f3eab77bd58d4f1f81cd8e7f1c95b0753c7f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079041"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a><span data-ttu-id="79927-102">\<methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz:\<list></span><span class="sxs-lookup"><span data-stu-id="79927-102">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion: \<list></span></span>

<span data-ttu-id="79927-103">Aşırı yüklenmiş bir yöntem çağrıldı, ancak metot bir daraltma dönüştürmesi olmadan belirtilen bağımsız değişkenlerin listesiyle eşleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="79927-103">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="79927-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="79927-104">To correct this error</span></span>  
  
1. <span data-ttu-id="79927-105">`Option Strict Off` belirtin.</span><span class="sxs-lookup"><span data-stu-id="79927-105">Specify `Option Strict Off`.</span></span>
  
2. <span data-ttu-id="79927-106">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzasıyla eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="79927-106">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79927-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79927-107">See also</span></span>

- [<span data-ttu-id="79927-108">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="79927-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="79927-109">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="79927-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

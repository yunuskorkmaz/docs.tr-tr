---
title: "Hiçbir erişilebilir aşırı yüklenmiş '<methodname>' bir daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılır: <list>"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: 230807eaa8e8bda7d8ca7b73d61dfc7a8fb40bf5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345501"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a><span data-ttu-id="39ae6-102">Hiçbir erişilebilir aşırı '\<yöntemAdı >' Bu bağımsız değişken bir daraltma dönüşümü olmadan çağrılabilir: \<listesi ></span><span class="sxs-lookup"><span data-stu-id="39ae6-102">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion: \<list></span></span>
<span data-ttu-id="39ae6-103">Aşırı yüklenmiş bir yöntemi çağrıldı, ancak yöntem bir daraltma dönüşümü olmadan sağlanan bağımsız değişken listesiyle eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="39ae6-103">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39ae6-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="39ae6-104">To correct this error</span></span>  
  
1. <span data-ttu-id="39ae6-105">Belirtin `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="39ae6-105">Specify `Option Strict Off`.</span></span>
  
2. <span data-ttu-id="39ae6-106">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzası eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="39ae6-106">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39ae6-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39ae6-107">See also</span></span>

- [<span data-ttu-id="39ae6-108">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="39ae6-108">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="39ae6-109">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="39ae6-109">Widening and Narrowing Conversions</span></span>](../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

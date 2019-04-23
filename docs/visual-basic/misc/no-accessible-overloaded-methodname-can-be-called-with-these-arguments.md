---
title: Hiçbir erişilebilir aşırı yüklenmiş '<methodname>' bir daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılır
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousMatch_NarrowingConversion1
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
ms.openlocfilehash: 5c55a767b1ea61117940b9c6f2a741174297274a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337870"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion"></a><span data-ttu-id="1700c-102">Hiçbir erişilebilir aşırı yüklenmiş '\<yöntemAdı >' bir daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılır</span><span class="sxs-lookup"><span data-stu-id="1700c-102">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion</span></span>
<span data-ttu-id="1700c-103">Aşırı yüklenmiş bir yöntemi çağrıldı, ancak yöntem bir daraltma dönüşümü olmadan sağlanan bağımsız değişkenler listesi ile eşleştirildi.</span><span class="sxs-lookup"><span data-stu-id="1700c-103">An overloaded method was called, but no method was matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1700c-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1700c-104">To correct this error</span></span>  
  
1. <span data-ttu-id="1700c-105">Belirtin `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="1700c-105">Specify `Option Strict Off`.</span></span>  
  
2. <span data-ttu-id="1700c-106">Bağımsız değişkenlerini bir aşırı yüklenmiş yöntemin imzası eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1700c-106">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1700c-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1700c-107">See also</span></span>

- [<span data-ttu-id="1700c-108">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="1700c-108">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="1700c-109">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="1700c-109">Widening and Narrowing Conversions</span></span>](../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

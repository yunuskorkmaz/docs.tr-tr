---
title: "Hiçbir erişilebilir aşırı yüklenmiş '&lt;methodname&gt;' bir daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılır: &lt;listesi&gt;"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: 2a34365c9f978f88e1e2b8c4cd4e673e6a49389b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495831"
---
# <a name="no-accessible-overloaded-ltmethodnamegt-can-be-called-with-these-arguments-without-a-narrowing-conversion-ltlistgt"></a><span data-ttu-id="a6df7-102">Hiçbir erişilebilir aşırı yüklenmiş '&lt;methodname&gt;' bir daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılır: &lt;listesi&gt;</span><span class="sxs-lookup"><span data-stu-id="a6df7-102">No accessible overloaded '&lt;methodname&gt;' can be called with these arguments without a narrowing conversion: &lt;list&gt;</span></span>
<span data-ttu-id="a6df7-103">Aşırı yüklenmiş bir yöntemi çağrıldı, ancak yöntem bir daraltma dönüşümü olmadan sağlanan bağımsız değişken listesiyle eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="a6df7-103">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6df7-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a6df7-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="a6df7-105">Belirtin `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="a6df7-105">Specify `Option Strict Off`.</span></span>
  
2.  <span data-ttu-id="a6df7-106">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzası eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a6df7-106">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6df7-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6df7-107">See also</span></span>
- [<span data-ttu-id="a6df7-108">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="a6df7-108">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="a6df7-109">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="a6df7-109">Widening and Narrowing Conversions</span></span>](../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

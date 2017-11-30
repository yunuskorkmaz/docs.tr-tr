---
title: "Hayır erişilebilir aşırı yüklenmiş &#39; &lt;methodname&gt;&#39; daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılamaz: &lt;listesi&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d0024289e64b97dc5c3ac253697d51194040a57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="no-accessible-overloaded-39ltmethodnamegt39-can-be-called-with-these-arguments-without-a-narrowing-conversion-ltlistgt"></a><span data-ttu-id="1a10f-102">Hayır erişilebilir aşırı yüklenmiş &#39; &lt;methodname&gt;&#39; daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılamaz: &lt;listesi&gt;</span><span class="sxs-lookup"><span data-stu-id="1a10f-102">No accessible overloaded &#39;&lt;methodname&gt;&#39; can be called with these arguments without a narrowing conversion: &lt;list&gt;</span></span>
<span data-ttu-id="1a10f-103">Aşırı yüklenmiş yöntemin çağrıldı, ancak sağlanan bağımsız değişkenler olmadan daraltma dönüşümü listesiyle yöntemi eşleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="1a10f-103">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a10f-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1a10f-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="1a10f-105">Belirtin `Option``Strict` `Off`.</span><span class="sxs-lookup"><span data-stu-id="1a10f-105">Specify `Option``Strict` `Off`.</span></span>  
  
2.  <span data-ttu-id="1a10f-106">Bağımsız değişkenlerini aşırı yüklenmiş yöntemin imzası eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1a10f-106">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a10f-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a10f-107">See Also</span></span>  
 [<span data-ttu-id="1a10f-108">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="1a10f-108">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="1a10f-109">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="1a10f-109">Widening and Narrowing Conversions</span></span>](../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

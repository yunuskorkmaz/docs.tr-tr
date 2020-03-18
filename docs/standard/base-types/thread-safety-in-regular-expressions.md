---
title: Normal İfadelerde İş Parçacığı Güvenliği
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: db25028e10872cfca08d28518c795414d06c5d49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124793"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="c67c8-102">Normal İfadelerde İş Parçacığı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c67c8-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="c67c8-103">Sınıfın <xref:System.Text.RegularExpressions.Regex> kendisi iş parçacığı güvenli ve değişmez (salt okunur).</span><span class="sxs-lookup"><span data-stu-id="c67c8-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="c67c8-104">Diğer bir diğer nokta, **Regex** nesneleri herhangi bir iş parçacığı üzerinde oluşturulabilir ve iş parçacıkları arasında paylaşılabilir; eşleşen yöntemler herhangi bir iş parçacığı çağrılabilir ve herhangi bir küresel durumu değiştirmek asla.</span><span class="sxs-lookup"><span data-stu-id="c67c8-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="c67c8-105">Ancak, **Regex** tarafından döndürülen sonuç nesneleri **(Match** ve **MatchCollection)** tek bir iş parçacığı üzerinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c67c8-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="c67c8-106">Bu nesnelerin çoğu mantıksal olarak değişmez olsa da, uygulamaları performansı artırmak için bazı sonuçların hesaplanmasını geciktirebilir ve sonuç olarak arayanların bunlara erişimi seri hale getirmelidir.</span><span class="sxs-lookup"><span data-stu-id="c67c8-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="c67c8-107">**Regex** sonuç nesnelerini birden çok iş parçacığı üzerinde paylaşma ihtiyacı varsa, bu nesneler eşitlenmiş yöntemlerini çağırarak iş parçacığı güvenli örneklerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="c67c8-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="c67c8-108">Tümumerators dışında, tüm düzenli ifade sınıfları iş parçacığı güvenli veya eşitlenmiş bir yöntem le iş parçacığı güvenli nesnelere dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="c67c8-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="c67c8-109">Sayısallaştırıcılar tek istisnadır.</span><span class="sxs-lookup"><span data-stu-id="c67c8-109">Enumerators are the only exception.</span></span> <span data-ttu-id="c67c8-110">Bir uygulama toplama sayısalatörler için çağrıları seri hale getirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="c67c8-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="c67c8-111">Kural, bir koleksiyon aynı anda birden fazla iş parçacığı üzerinde numaralandırılabilir, sen enumerator tarafından geçen koleksiyonun kök nesnesi üzerinde numaralandırma yöntemleri eşitlemek gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="c67c8-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c67c8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c67c8-112">See also</span></span>

- [<span data-ttu-id="c67c8-113">.NET Düzenli İfadeler</span><span class="sxs-lookup"><span data-stu-id="c67c8-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)

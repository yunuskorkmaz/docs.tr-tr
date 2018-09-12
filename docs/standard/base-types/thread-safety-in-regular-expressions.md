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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0bcab0757bc48f6a8216dd5878f0289e49a275
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44493894"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="05f74-102">Normal İfadelerde İş Parçacığı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="05f74-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="05f74-103"><xref:System.Text.RegularExpressions.Regex> Sınıfının kendisini güvenli ve sabit (salt okunur) iş parçacığıdır.</span><span class="sxs-lookup"><span data-stu-id="05f74-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="05f74-104">Diğer bir deyişle, **Regex** nesneler üzerinde herhangi bir iş parçacığı oluşturulabilir ve iş parçacıkları arasında paylaşılan; eşleme yöntemlerini herhangi bir iş parçacığından çağrılabilir ve hiçbir zaman herhangi bir genel durumu değiştirme.</span><span class="sxs-lookup"><span data-stu-id="05f74-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="05f74-105">Ancak, sonuç nesnelerini (**eşleşme** ve **MatchCollection**) tarafından döndürülen **Regex** tek bir iş parçacığında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05f74-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="05f74-106">Çoğu bu nesnelerin mantıksal sabittir, ancak kendi uygulamalarını hesaplama performansını artırmak için bazı sonuçları geciktirebilir ve sonuç olarak, Arayanların onlara yönelik erişimi seri gerekir.</span><span class="sxs-lookup"><span data-stu-id="05f74-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="05f74-107">Paylaşımı yapmanız ise **Regex** sonuç nesneleri birden çok iş parçacığında bu nesneler dönüştürülebilir iş parçacığı açısından güvenli örneklerine eşitlenmiş kendi yöntemlerini çağırarak.</span><span class="sxs-lookup"><span data-stu-id="05f74-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="05f74-108">Numaralandırıcılar dışında tüm normal ifade sınıfları iş parçacığı güvenlidir veya iş parçacığı nesneleri eşitlenmiş bir yöntemle dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="05f74-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="05f74-109">Numaralandırıcılar tek özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="05f74-109">Enumerators are the only exception.</span></span> <span data-ttu-id="05f74-110">Uygulama koleksiyonu numaralandırıcılar çağrıları seri gerekir.</span><span class="sxs-lookup"><span data-stu-id="05f74-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="05f74-111">Bir koleksiyon birden fazla iş parçacığında aynı anda numaralandırılabilir, numaralandırıcı yöntemlerde geçiş tarafından numaralandırıcıyı koleksiyonun kök nesnesi eşitlemeniz gerekir kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="05f74-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f74-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05f74-112">See also</span></span>

- [<span data-ttu-id="05f74-113">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="05f74-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)

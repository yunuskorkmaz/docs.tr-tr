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
ms.openlocfilehash: fbcaaf4942f8af1d6c1de52ff5bc11317318f319
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290895"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="a072e-102">Normal İfadelerde İş Parçacığı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a072e-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="a072e-103"><xref:System.Text.RegularExpressions.Regex>Sınıfın kendisi iş parçacığı güvenlidir ve sabittir (salt okunurdur).</span><span class="sxs-lookup"><span data-stu-id="a072e-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="a072e-104">Diğer bir deyişle, **Regex** nesneleri herhangi bir iş parçacığında oluşturulabilir ve iş parçacıkları arasında paylaşılabilir; eşleşen Yöntemler herhangi bir iş parçacığından çağrılabilir ve hiçbir şekilde hiçbir genel durumu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="a072e-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="a072e-105">Ancak, **Regex** tarafından döndürülen sonuç nesneleri (**Match** ve **MatchCollection**) tek bir iş parçacığında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a072e-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="a072e-106">Bu nesnelerin birçoğu mantıksal olarak sabit olsa da, uygulamaları performansı artırmak için bazı sonuçların hesaplamasını erteleyebilir ve sonuç olarak, arayanların bunlara erişimi serileştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a072e-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="a072e-107">Birden çok iş parçacığında **Regex** sonuç nesnelerini paylaşma gereksinimi varsa, bu nesneler eşitlenmiş yöntemleri çağırarak iş parçacığı açısından güvenli örneklere dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="a072e-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="a072e-108">Numaralandırıcılar hariç, tüm normal ifade sınıfları iş parçacığı açısından güvenlidir veya eşitlenmiş bir yöntem tarafından iş parçacığı güvenli nesnelerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="a072e-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="a072e-109">Numaralandırıcılar tek istisnadır.</span><span class="sxs-lookup"><span data-stu-id="a072e-109">Enumerators are the only exception.</span></span> <span data-ttu-id="a072e-110">Uygulama, çağrıları koleksiyon numaralandırıcılara serileştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="a072e-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="a072e-111">Kural, bir koleksiyonun birden fazla iş parçacığında aynı anda numaralandırılabilir olması, Numaralandırıcı tarafından geçilen koleksiyonun kök nesnesindeki Numaralandırıcı yöntemlerini eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a072e-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a072e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a072e-112">See also</span></span>

- [<span data-ttu-id="a072e-113">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a072e-113">.NET Regular Expressions</span></span>](regular-expressions.md)

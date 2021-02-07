---
description: 'Daha fazla bilgi edinin: normal Ifadelerde Iş parçacığı güvenliği'
title: Normal İfadelerde İş Parçacığı Güvenliği
ms.date: 03/30/2017
ms.topic: conceptual
helpviewer_keywords:
- .NET regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: 93aaed60179c043e414ac0d296722bc397b7e771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702892"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="254fc-103">Normal İfadelerde İş Parçacığı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="254fc-103">Thread Safety in Regular Expressions</span></span>

<span data-ttu-id="254fc-104"><xref:System.Text.RegularExpressions.Regex>Sınıfın kendisi iş parçacığı güvenlidir ve sabittir (salt okunurdur).</span><span class="sxs-lookup"><span data-stu-id="254fc-104">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="254fc-105">Diğer bir deyişle, **Regex** nesneleri herhangi bir iş parçacığında oluşturulabilir ve iş parçacıkları arasında paylaşılabilir; eşleşen Yöntemler herhangi bir iş parçacığından çağrılabilir ve hiçbir şekilde hiçbir genel durumu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="254fc-105">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="254fc-106">Ancak, **Regex** tarafından döndürülen sonuç nesneleri (**Match** ve **MatchCollection**) tek bir iş parçacığında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="254fc-106">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="254fc-107">Bu nesnelerin birçoğu mantıksal olarak sabit olsa da, uygulamaları performansı artırmak için bazı sonuçların hesaplamasını erteleyebilir ve sonuç olarak, arayanların bunlara erişimi serileştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="254fc-107">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="254fc-108">Birden çok iş parçacığında **Regex** sonuç nesnelerini paylaşma gereksinimi varsa, bu nesneler eşitlenmiş yöntemleri çağırarak iş parçacığı açısından güvenli örneklere dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="254fc-108">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="254fc-109">Numaralandırıcılar hariç, tüm normal ifade sınıfları iş parçacığı açısından güvenlidir veya eşitlenmiş bir yöntem tarafından iş parçacığı güvenli nesnelerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="254fc-109">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="254fc-110">Numaralandırıcılar tek istisnadır.</span><span class="sxs-lookup"><span data-stu-id="254fc-110">Enumerators are the only exception.</span></span> <span data-ttu-id="254fc-111">Uygulama, çağrıları koleksiyon numaralandırıcılara serileştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="254fc-111">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="254fc-112">Kural, bir koleksiyonun birden fazla iş parçacığında aynı anda numaralandırılabilir olması, Numaralandırıcı tarafından geçilen koleksiyonun kök nesnesindeki Numaralandırıcı yöntemlerini eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="254fc-112">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="254fc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="254fc-113">See also</span></span>

- [<span data-ttu-id="254fc-114">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="254fc-114">.NET Regular Expressions</span></span>](regular-expressions.md)

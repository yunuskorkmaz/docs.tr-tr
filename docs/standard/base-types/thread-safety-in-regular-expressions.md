---
title: "Normal İfadelerde İş Parçacığı Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4cfa24da8083eac01275ad76f5c2db974b39a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="6baa3-102">Normal İfadelerde İş Parçacığı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6baa3-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="6baa3-103"><xref:System.Text.RegularExpressions.Regex> Sınıfının kendisini iş parçacığı güvenli ve değişmez (salt okunur) değil.</span><span class="sxs-lookup"><span data-stu-id="6baa3-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="6baa3-104">Diğer bir deyişle, **Regex** nesneler hiçbir iş parçacığı üzerinde oluşturulan ve iş parçacıkları arasında paylaşılan; eşleşen yöntem herhangi bir iş parçacığından çağrılabilir ve hiçbir zaman herhangi bir genel durum alter.</span><span class="sxs-lookup"><span data-stu-id="6baa3-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="6baa3-105">Ancak, sonuç nesnelerini (**eşleşme** ve **MatchCollection**) tarafından döndürülen **Regex** tek bir iş parçacığında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6baa3-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="6baa3-106">Bu nesnelerin çoğunu mantıksal olarak değişmez olsa da, kendi uygulamalarını performansını artırmak için bazı sonuçlarının hesaplama geciktirebilir ve sonuç olarak, arayanlar onlara erişimi seri gerekir.</span><span class="sxs-lookup"><span data-stu-id="6baa3-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="6baa3-107">Paylaşmak için bir gereksinimi varsa **Regex** sonuç nesneleri birden çok iş parçacığı üzerinde bu nesnelerin dönüştürülebilir iş parçacığı örneklerine eşitlenmiş yöntemleriyle çağırarak.</span><span class="sxs-lookup"><span data-stu-id="6baa3-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="6baa3-108">Numaralandırmalar, hariç olmak üzere tüm normal ifade sınıfları iş parçacığı açısından güvenlidir veya iş parçacığı nesneleri eşitlenmiş bir yöntemle dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="6baa3-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="6baa3-109">Numaralandırmalar tek özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="6baa3-109">Enumerators are the only exception.</span></span> <span data-ttu-id="6baa3-110">Bir uygulama çağrıları koleksiyonunun numaralandırmalar için seri hale gerekir.</span><span class="sxs-lookup"><span data-stu-id="6baa3-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="6baa3-111">Bir koleksiyon birden çok iş parçacığı üzerinde aynı anda numaralandırılabilecek, numaralandırıcı yöntemleri tarafından Numaralandırıcı geçiş koleksiyonunun kök nesnede eşitlenmesi gerektiğini kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="6baa3-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6baa3-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6baa3-112">See Also</span></span>  
 [<span data-ttu-id="6baa3-113">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="6baa3-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)

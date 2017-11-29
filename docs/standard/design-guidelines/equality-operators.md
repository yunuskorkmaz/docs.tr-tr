---
title: "Eşitlik İşleçleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55c0505f5a06dfc87897fa59e9d6083cbd63c8ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="equality-operators"></a><span data-ttu-id="0862a-102">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="0862a-102">Equality Operators</span></span>
<span data-ttu-id="0862a-103">Bu bölümde tekrar yüklemesi eşitlik işleçleri açıklanır ve başvurduğu `operator==` ve `operator!=` eşitlik işleçleri olarak.</span><span class="sxs-lookup"><span data-stu-id="0862a-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="0862a-104">**X yok** eşitlik işleçleri ve diğer aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="0862a-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="0862a-105">**✓ YAPMAK** emin <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçleri tam olarak aynı semantiği ve benzer performans özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0862a-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="0862a-106">Bu genellikle anlamına `Object.Equals` eşitlik işleçleri aşırı zaman geçersiz kılınacak gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="0862a-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="0862a-107">**KAÇININ x** eşitlik işleçleri özel durumları atma.</span><span class="sxs-lookup"><span data-stu-id="0862a-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="0862a-108">Örneğin, bağımsız değişkenlerden biri atma yerine null ise false döndürür `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="0862a-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="0862a-109">Değer türleri üzerinde eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="0862a-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="0862a-110">**✓ YAPMAK** eşitlik anlamlı ise, değer türleri üzerinde eşitlik işleçleri aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="0862a-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="0862a-111">Çoğu programlama dillerinde hiçbir varsayılan uygulaması olduğundan `operator==` değer türleri için.</span><span class="sxs-lookup"><span data-stu-id="0862a-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="0862a-112">Başvuru türleri üzerinde eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="0862a-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="0862a-113">**KAÇININ x** kesilebilir başvuru türleri üzerinde eşitlik işleçleri aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="0862a-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="0862a-114">Birçok dilin başvuru türleri için yerleşik eşitlik işleçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0862a-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="0862a-115">Yerleşik genellikle başvuru eşitliği işleçler ve varsayılan davranışı için değer eşitliği değiştirildiğinde, geliştiricilerin çoğu Şaşkın.</span><span class="sxs-lookup"><span data-stu-id="0862a-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="0862a-116">Girişi çok referans eşitlik ve değer eşitliği arasındaki fark zorlaştıran çünkü bu sorunu değişmez başvuru türlerinde azalır.</span><span class="sxs-lookup"><span data-stu-id="0862a-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="0862a-117">**KAÇININ x** uygulama önemli ölçüde daha yavaş, başvuru eşitliği olacaksa başvuru türlerinde eşitlik işleçleri aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="0862a-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="0862a-118">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="0862a-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0862a-119">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="0862a-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0862a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0862a-120">See Also</span></span>  
 [<span data-ttu-id="0862a-121">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0862a-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="0862a-122">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0862a-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)

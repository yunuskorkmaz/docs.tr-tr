---
title: Geri aramalar ve olayları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6a6851d1be543fe356827cad67b28cafdc9e56c2
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="events-and-callbacks"></a><span data-ttu-id="a829e-102">Geri aramalar ve olayları</span><span class="sxs-lookup"><span data-stu-id="a829e-102">Events and Callbacks</span></span>
<span data-ttu-id="a829e-103">Geri aramalar kullanıcı kodu bir temsilci aracılığıyla geri çağırmak için bir çerçeve izin genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="a829e-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="a829e-104">Bu temsilci genellikle framework bir yöntemin parametre geçirildi.</span><span class="sxs-lookup"><span data-stu-id="a829e-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="a829e-105">(Bir olay işleyicisi) temsilci sağlama için uygun ve tutarlı sözdizimi destekleyen bir özel durum geri aramalar, olaylardır.</span><span class="sxs-lookup"><span data-stu-id="a829e-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="a829e-106">Ayrıca, Visual Studio'nun deyim tamamlama ve tasarımcıları olay tabanlı API'lerini kullanarak Yardım sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a829e-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="a829e-107">(Bkz [olay tasarım](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="a829e-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="a829e-108">**✓ DÜŞÜNÜN** çerçevesi tarafından yürütülecek özel kod sağlamak için kullanıcıların izin vermek için geri çağırmaları kullanma.</span><span class="sxs-lookup"><span data-stu-id="a829e-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="a829e-109">**✓ DÜŞÜNÜN** framework nesne odaklı tasarım anlamak için gerek kalmadan davranışını özelleştirmek kullanıcıların olayları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a829e-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="a829e-110">**✓ YAPMAK** daha geniş bir grup geliştiriciler için tanıdık ve Visual Studio deyim tamamlama ile tümleşik olduğundan olayları düz geri aramalar tercih.</span><span class="sxs-lookup"><span data-stu-id="a829e-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="a829e-111">**KAÇININ x** geri aramalar performans duyarlı API'leri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a829e-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="a829e-112">**✓ YAPMAK** yeni `Func<...>`, `Action<...>`, veya `Expression<...>` API'leri ile geri aramalar tanımlarken özel temsilciler yerine türleri.</span><span class="sxs-lookup"><span data-stu-id="a829e-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="a829e-113">`Func<...>` ve `Action<...>` genel temsilciler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a829e-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="a829e-114">`Expression<...>` derlenmiş ve daha sonra ancak çalışma zamanında da çağrılan temsil işlev tanımları sıralanabilir ve uzak işlemler geçirildi.</span><span class="sxs-lookup"><span data-stu-id="a829e-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="a829e-115">**✓ YAPMAK** ölçmek ve performans etkilerini kullanmanın `Expression<...>`, yerine `Func<...>` ve `Action<...>` temsilciler.</span><span class="sxs-lookup"><span data-stu-id="a829e-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="a829e-116">`Expression<...>` türleridir çoğu durumda mantıksal olarak eşdeğer `Func<...>` ve `Action<...>` temsilciler.</span><span class="sxs-lookup"><span data-stu-id="a829e-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="a829e-117">Bunlar arasındaki temel fark temsilcileri yerel işlem senaryolarda kullanılması amaçlanmıştır olan; ifadeler faydalı ve uzak işlem veya makine ifadesinde değerlendirmek mümkün olduğu durumlarda yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a829e-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="a829e-118">**✓ YAPMAK** temsilci çağırarak rastgele kod yürütülmekte olduğunu anlamak ve güvenlik, doğruluk ve uyumluluk varsa sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a829e-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="a829e-119">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="a829e-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a829e-120">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="a829e-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a829e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a829e-121">See Also</span></span>  
 [<span data-ttu-id="a829e-122">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="a829e-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="a829e-123">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a829e-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

---
title: Etkinlikler ve Geri Aramalar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: KrzysztofCwalina
ms.openlocfilehash: 3609d6ac4847cb081740fd698869df4976f83f8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960413"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="e3d42-102">Etkinlikler ve Geri Aramalar</span><span class="sxs-lookup"><span data-stu-id="e3d42-102">Events and Callbacks</span></span>
<span data-ttu-id="e3d42-103">Geri çağırmalar, geri bir temsilci yoluyla kullanıcı kodu çağırmak bir çerçeve izin genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="e3d42-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="e3d42-104">Bu Temsilciler, genellikle bir yöntemin bir parametresi aracılığıyla framework geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e3d42-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="e3d42-105">Temsilci (bir olay işleyicisi) sağlama için kullanışlı ve tutarlı bir söz dizimi destekleyen bir özel durum geri çağırmalar olaylardır.</span><span class="sxs-lookup"><span data-stu-id="e3d42-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="e3d42-106">Ayrıca, Visual Studio'nun deyim tamamlama ve tasarımcılar olay-tabanlı API'ler kullanarak Yardım sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e3d42-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="e3d42-107">(Bkz [olay tasarımı](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="e3d42-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="e3d42-108">**✓ CONSIDER** çerçevesi tarafından yürütülecek özel kod sağlamak için kullanıcıların izin vermek için geri çağırmaları kullanma.</span><span class="sxs-lookup"><span data-stu-id="e3d42-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="e3d42-109">**✓ CONSIDER** framework nesne odaklı tasarım anlamak için gerek kalmadan davranışını özelleştirmek kullanıcıların olayları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="e3d42-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="e3d42-110">**✓ DO** daha geniş bir grup geliştiriciler için tanıdık ve Visual Studio deyim tamamlama ile tümleşik olduğundan olayları düz geri aramalar tercih.</span><span class="sxs-lookup"><span data-stu-id="e3d42-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="e3d42-111">**X AVOID** geri aramalar performans duyarlı API'leri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="e3d42-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="e3d42-112">**✓ DO** yeni `Func<...>`, `Action<...>`, veya `Expression<...>` API'leri ile geri aramalar tanımlarken özel temsilciler yerine türleri.</span><span class="sxs-lookup"><span data-stu-id="e3d42-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="e3d42-113">`Func<...>` ve `Action<...>` genel temsilciler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e3d42-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="e3d42-114">`Expression<...>` derlenmiş ve daha sonra ancak çalışma zamanında da çağrılan temsil işlev tanımları sıralanabilir ve uzak işlemler geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e3d42-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="e3d42-115">**✓ DO** ölçmek ve performans etkilerini kullanmanın `Expression<...>`, yerine `Func<...>` ve `Action<...>` temsilciler.</span><span class="sxs-lookup"><span data-stu-id="e3d42-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="e3d42-116">`Expression<...>` Çoğu durumda mantıksal eşdeğer türleridir `Func<...>` ve `Action<...>` temsilciler.</span><span class="sxs-lookup"><span data-stu-id="e3d42-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="e3d42-117">Aralarındaki temel fark, temsilciler yerel işlem senaryolarda kullanılması amaçlanmıştır olan; ifadeleri yararlı ve uzak işlem veya makine ifadeyi değerlendirmek mümkün olduğu durumlarda yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e3d42-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="e3d42-118">**✓ DO** temsilci çağırarak rastgele kod yürütülmekte olduğunu anlamak ve güvenlik, doğruluk ve uyumluluk varsa sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e3d42-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="e3d42-119">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e3d42-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e3d42-120">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="e3d42-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d42-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3d42-121">See also</span></span>

- [<span data-ttu-id="e3d42-122">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="e3d42-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="e3d42-123">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e3d42-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

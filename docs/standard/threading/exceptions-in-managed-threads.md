---
title: "Yönetilen İş Parçacıklarında Özel Durumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f68a7aebdb1625b149287d70fd91c2108a658b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="a4af8-102">Yönetilen İş Parçacıklarında Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="a4af8-102">Exceptions in Managed Threads</span></span>
<span data-ttu-id="a4af8-103">.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanı en işlenmeyen özel durumlar doğal olarak devam etmek için iş parçacığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4af8-103">Starting with the .NET Framework version 2.0, the common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="a4af8-104">Çoğu durumda bu işlenmeyen bir özel durum için uygulamanın neden olduğunu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a4af8-104">In most cases this means that the unhandled exception causes the application to terminate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4af8-105">Bu önemli bir backstop sağlamak için birçok işlenmeyen özel durumlar 1.0 ve 1.1, .NET Framework sürümleri farklıdır — Örneğin, iş parçacığı havuzu iş parçacıklarında özel durumlar işlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="a4af8-105">This is a significant change from the .NET Framework versions 1.0 and 1.1, which provide a backstop for many unhandled exceptions — for example, unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="a4af8-106">Bkz: [değiştirmek önceki sürümlerden](#ChangeFromPreviousVersions) bu konuda daha sonra.</span><span class="sxs-lookup"><span data-stu-id="a4af8-106">See [Change from Previous Versions](#ChangeFromPreviousVersions) later in this topic.</span></span>  
  
 <span data-ttu-id="a4af8-107">Ortak dil çalışma zamanı program akışı denetimi için kullanılan bir backstop belirli işlenmeyen özel durumlar sağlar:</span><span class="sxs-lookup"><span data-stu-id="a4af8-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
-   <span data-ttu-id="a4af8-108">A <xref:System.Threading.ThreadAbortException> bir iş parçacığı, çünkü atılır <xref:System.Threading.Thread.Abort%2A> çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="a4af8-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
-   <span data-ttu-id="a4af8-109">Bir <xref:System.AppDomainUnloadedException> iş parçacığı Yürütülüyor uygulama etki alanı bellekten çünkü bir iş parçacığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a4af8-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
-   <span data-ttu-id="a4af8-110">Ortak dil çalışma zamanı ya da bir ana bilgisayar işlemi iş parçacığı bir iç özel durum atma tarafından sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="a4af8-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="a4af8-111">Bu özel durumlar hiçbirini ortak dil çalışma zamanı tarafından oluşturulan iş parçacıklarında işlenmemiş, özel iş parçacığı sonlanır, ancak ortak dil çalışma zamanı devam etmek özel durum izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="a4af8-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="a4af8-112">Bu özel durumlar ana iş parçacığı veya yönetilmeyen koddan çalışma zamanı girilen iş parçacığı işlenmeyen varsa, bunlar normalde, uygulamanın sonlandırılmasıyla kaynaklanan devam edin.</span><span class="sxs-lookup"><span data-stu-id="a4af8-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4af8-113">Yönetilen kod bir özel durum işleyici yüklemek için bir fırsat dolmadığı önce işlenmeyen bir özel durum atmak için çalışma zamanı için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a4af8-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="a4af8-114">Yönetilen kod gibi özel bir durumu işlemek için hiçbir şansınız olsa bile, özel durum doğal olarak devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a4af8-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="a4af8-115">Geliştirme sırasında sorunları iş parçacığı oluşturma gösterme</span><span class="sxs-lookup"><span data-stu-id="a4af8-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="a4af8-116">İş parçacığı uygulama sonlandırma olmadan sessizce başarısız olmasına izin verildiğinde programlama ciddi sorunlar algılanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a4af8-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="a4af8-117">Bu, hizmetler ve uzun süre çalışan diğer uygulamalar için belirli bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="a4af8-117">This is a particular problem for services and other applications which run for extended periods.</span></span> <span data-ttu-id="a4af8-118">Başarısız iş parçacıkları gibi program durumu kademeli olarak bozulur.</span><span class="sxs-lookup"><span data-stu-id="a4af8-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="a4af8-119">Uygulama performansı düşebilir veya uygulama askıda.</span><span class="sxs-lookup"><span data-stu-id="a4af8-119">Application performance may degrade, or the application might hang.</span></span>  
  
 <span data-ttu-id="a4af8-120">İşletim sistemi program sonlanana kadar doğal olarak, devam etmek için iş parçacığı işlenmeyen özel durumlar izin vererek bu tür sorunları geliştirme ve sınama sırasında kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a4af8-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="a4af8-121">Program sonlandırmalar hata ayıklama desteği üzerinde hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="a4af8-121">Error reports on program terminations support debugging.</span></span>  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a><span data-ttu-id="a4af8-122">Önceki sürümlerden değiştirme</span><span class="sxs-lookup"><span data-stu-id="a4af8-122">Change from Previous Versions</span></span>  
 <span data-ttu-id="a4af8-123">Yönetilen iş parçacığı için en önemli değişiklik ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="a4af8-123">The most significant change pertains to managed threads.</span></span> <span data-ttu-id="a4af8-124">.NET Framework sürüm 1.0 ve 1.1, ortak dil çalışma zamanı aşağıdaki durumlarda işlenmeyen özel durumlar için bir backstop sağlar:</span><span class="sxs-lookup"><span data-stu-id="a4af8-124">In the .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
-   <span data-ttu-id="a4af8-125">Bir iş parçacığı havuzu iş parçacığı işlenmeyen bir özel olarak bu tür bir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="a4af8-125">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="a4af8-126">Bir görev, işlemiyor bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve iş parçacığı iş parçacığı havuzuna döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4af8-126">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
-   <span data-ttu-id="a4af8-127">Bir iş parçacığı işlenmeyen özel durum ile oluşturulmuş böyle bir şey olduğunu <xref:System.Threading.Thread.Start%2A> yöntemi <xref:System.Threading.Thread> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4af8-127">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="a4af8-128">Böyle bir iş parçacığı üzerinde çalışan kodu değil işleyecek bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve iş parçacığı düzgün biçimde sonlanır.</span><span class="sxs-lookup"><span data-stu-id="a4af8-128">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
-   <span data-ttu-id="a4af8-129">Sonlandırıcı iş parçacığı işlenmeyen özel durum olarak böyle bir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="a4af8-129">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="a4af8-130">Bir sonlandırıcı olmayan işleyecek bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve sonlandırıcılar çalışmasını devam ettirmek sonlandırıcıyı iş parçacığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4af8-130">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="a4af8-131">Yönetilen iş parçacığı ön plan veya arka plan durumunu bu davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="a4af8-131">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="a4af8-132">İş parçacıklarını yönetilmeyen kodunda kaynaklanan işlenmeyen özel durumlar için daha hafif farktır.</span><span class="sxs-lookup"><span data-stu-id="a4af8-132">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="a4af8-133">Çalışma zamanı JIT-ekleme iletişim yönetilen özel durumlar veya aracılığıyla yerel koda geçtiğinde iş parçacığı yerel özel durumlar için işletim sistemi iletişim etkisiz hale getiren.</span><span class="sxs-lookup"><span data-stu-id="a4af8-133">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="a4af8-134">Tüm durumlarda işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="a4af8-134">The process terminates in all cases.</span></span>  
  
### <a name="migrating-code"></a><span data-ttu-id="a4af8-135">Geçirme kodu</span><span class="sxs-lookup"><span data-stu-id="a4af8-135">Migrating Code</span></span>  
 <span data-ttu-id="a4af8-136">Genel olarak, böylece bunlar sabit değişikliği önceden tanınmayan programlama sorunlarını açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a4af8-136">In general, the change will expose previously unrecognized programming problems so that they can be fixed.</span></span> <span data-ttu-id="a4af8-137">Bazı durumlarda, ancak programcıları örneğin iş parçacıklarını sonlandırma çalışma zamanı backstop avantajlarından gerçekleştirmişsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4af8-137">In some cases, however, programmers might have taken advantage of the runtime backstop, for example to terminate threads.</span></span> <span data-ttu-id="a4af8-138">Durum bağlı olarak, aşağıdaki geçiş stratejiler birini dikkate alın:</span><span class="sxs-lookup"><span data-stu-id="a4af8-138">Depending on the situation, they should consider one of the following migration strategies:</span></span>  
  
-   <span data-ttu-id="a4af8-139">Sinyal alındığında iş parçacığı düzgün biçimde çıkar şekilde kodu yeniden yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4af8-139">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
-   <span data-ttu-id="a4af8-140">Kullanım <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> iş parçacığı iptal etmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="a4af8-140">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
-   <span data-ttu-id="a4af8-141">İşlem sonlandırma devam edebilirsiniz böylece bir iş parçacığı durdurulması gerekir, böylece işlem Çıkışta otomatik olarak sona erdi iş parçacığı bir arka plan iş parçacığı olun.</span><span class="sxs-lookup"><span data-stu-id="a4af8-141">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
 <span data-ttu-id="a4af8-142">Tüm durumlarda stratejisi özel durumlar için tasarım yönergeleri izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="a4af8-142">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="a4af8-143">Bkz: [tasarım yönergeleri için özel durumları](../../../docs/standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="a4af8-143">See [Design Guidelines for Exceptions](../../../docs/standard/design-guidelines/exceptions.md).</span></span>  
  
### <a name="application-compatibility-flag"></a><span data-ttu-id="a4af8-144">Uygulama uyumluluk bayrağı</span><span class="sxs-lookup"><span data-stu-id="a4af8-144">Application Compatibility Flag</span></span>  
 <span data-ttu-id="a4af8-145">Geçici uyumluluk ölçü olarak bir uyumluluk bayrağı Yöneticiler yerleştirebilirsiniz `<runtime>` uygulama yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="a4af8-145">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="a4af8-146">Bu, 1.0 ve 1.1 sürümleri davranışa geri dönmek ortak dil çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="a4af8-146">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="a4af8-147">Ana bilgisayar geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a4af8-147">Host Override</span></span>  
 <span data-ttu-id="a4af8-148">.NET Framework sürüm 2. 0'da, yönetilmeyen bir ana bilgisayar kullanabilirsiniz [Iclrpolicymanager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) varsayılan geçersiz kılmak için barındırma API arabiriminde işlenmeyen özel durum ilkesi ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a4af8-148">In the .NET Framework version 2.0, an unmanaged host can use the [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="a4af8-149">[Iclrpolicymanager::setunhandledexceptionpolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) işlevi işlenmeyen özel durumlar için ilkesini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4af8-149">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4af8-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4af8-150">See Also</span></span>  
 [<span data-ttu-id="a4af8-151">Yönetilen İş Parçacığı Oluşturma Temelleri</span><span class="sxs-lookup"><span data-stu-id="a4af8-151">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)

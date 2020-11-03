---
title: Yönetilen İş Parçacıklarında Özel Durumlar
description: İşlenmemiş özel durumların .NET 'te nasıl işlendiğini görün. İşlenmemiş iş parçacığı özel durumlarının çoğu doğal olarak devam edip uygulama sonlandırmasına yol açabilir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET],unhandled exceptions
- threading [.NET],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: b7cf7e94156eedc82c7ec5c863ee013b75d22e73
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188334"
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="c5d8b-104">Yönetilen iş parçacıklarında özel durumlar</span><span class="sxs-lookup"><span data-stu-id="c5d8b-104">Exceptions in managed threads</span></span>

<span data-ttu-id="c5d8b-105">Ortak dil çalışma zamanı, iş parçacıklarında işlenmemiş özel durumların çoğunu doğal olarak devam etmesine izin verir</span><span class="sxs-lookup"><span data-stu-id="c5d8b-105">The common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="c5d8b-106">Çoğu durumda bu, işlenmeyen özel durumun uygulamanın sonlandırılmasına neden olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-106">In most cases this means that the unhandled exception causes the application to terminate.</span></span>
  
<span data-ttu-id="c5d8b-107">Ortak dil çalışma zamanı, program akışını denetlemek için kullanılan, işlenmemiş özel durumlar için bir geri durağı sağlar:</span><span class="sxs-lookup"><span data-stu-id="c5d8b-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
- <span data-ttu-id="c5d8b-108"><xref:System.Threading.ThreadAbortException>Çağrıldığında bir iş parçacığında oluşturulur <xref:System.Threading.Thread.Abort%2A> .</span><span class="sxs-lookup"><span data-stu-id="c5d8b-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
- <span data-ttu-id="c5d8b-109">İş parçacığı üzerinde <xref:System.AppDomainUnloadedException> yürütülmekte olan uygulama etki alanı kaldırılmakta olduğundan bir iş parçacığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
- <span data-ttu-id="c5d8b-110">Ortak dil çalışma zamanı veya bir konak işlemi, bir iç özel durum oluşturarak iş parçacığını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="c5d8b-111">Bu özel durumların herhangi biri ortak dil çalışma zamanı tarafından oluşturulan iş parçacıklarında yakalanmadıysa, özel durum iş parçacığını sonlandırır, ancak ortak dil çalışma zamanı özel durumun daha fazla devam edeceğine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="c5d8b-112">Bu özel durumlar ana iş parçacığında işlenmemiş veya yönetilmeyen koddan çalışma zamanına giren iş parçacıklarında, normalde devam ederler ve uygulamanın sonlandırmasına yol açar.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5d8b-113">Yönetilen herhangi bir kodun özel durum işleyicisi yüklemesi şansı olmadan önce, çalışma zamanının işlenmeyen bir özel durum oluşturması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="c5d8b-114">Yönetilen kodun böyle bir özel durumu işleme şansı olmasa da, özel durumun doğal olarak devam etmesi için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="c5d8b-115">Geliştirme sırasında Iş parçacığı sorunlarını gösterme</span><span class="sxs-lookup"><span data-stu-id="c5d8b-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="c5d8b-116">İş parçacıklarının sessizce başarısız olmasına izin verildiğinde, uygulamayı sonlandırmadan ciddi programlama sorunları saptanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="c5d8b-117">Bu, gelişmiş dönemler için çalışan hizmetler ve diğer uygulamalar için özel bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-117">This is a particular problem for services and other applications that run for extended periods.</span></span> <span data-ttu-id="c5d8b-118">İş parçacıkları başarısız olduğu sürece program durumu yavaş yavaş bozulur.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="c5d8b-119">Uygulama performansı düşebilir veya uygulama yanıt vermiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-119">Application performance may degrade, or the application might become unresponsive.</span></span>  
  
 <span data-ttu-id="c5d8b-120">İşletim sistemi programı sonlandırana kadar, iş parçacıklarında işlenmeyen özel durumların doğal olarak devam etmesini sağlamak, geliştirme ve test sırasında böyle sorunlar ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="c5d8b-121">Program sonlandırışları üzerindeki hata raporları hata ayıklamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-121">Error reports on program terminations support debugging.</span></span>  
  
## <a name="change-from-previous-versions"></a><span data-ttu-id="c5d8b-122">Önceki sürümlerden Değiştir</span><span class="sxs-lookup"><span data-stu-id="c5d8b-122">Change from previous versions</span></span>

<span data-ttu-id="c5d8b-123">.NET Framework sürüm 1,0 ve 1,1 ' de, ortak dil çalışma zamanı, işlenmemiş özel durumlar için aşağıdaki durumlarda bir geri durağı sağlar:</span><span class="sxs-lookup"><span data-stu-id="c5d8b-123">In .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
- <span data-ttu-id="c5d8b-124">İş parçacığı havuzu iş parçacığında işlenmemiş özel durum gibi bir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-124">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="c5d8b-125">Bir görev, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve iş parçacığını iş parçacığı havuzuna döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-125">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
- <span data-ttu-id="c5d8b-126">Sınıf yöntemiyle oluşturulan bir iş parçacığında işlenmemiş özel durum olarak böyle bir şey yoktur <xref:System.Threading.Thread.Start%2A> <xref:System.Threading.Thread> .</span><span class="sxs-lookup"><span data-stu-id="c5d8b-126">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="c5d8b-127">Böyle bir iş parçacığı üzerinde çalışan kod, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve sonra iş parçacığını normal şekilde sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-127">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
- <span data-ttu-id="c5d8b-128">Sonlandırıcı iş parçacığında işlenmeyen bir özel durum yok.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-128">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="c5d8b-129">Bir Sonlandırıcı, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve sonra Sonlandırıcı iş parçacığının sonlandırıcıları çalıştırmaya sürdürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-129">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="c5d8b-130">Yönetilen bir iş parçacığının ön plan veya arka plan durumu bu davranışı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-130">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="c5d8b-131">Yönetilmeyen kodda oluşan iş parçacıklarında işlenmeyen özel durumlar için, fark daha hafif olur.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-131">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="c5d8b-132">Çalışma zamanı JıT-iliştirme iletişim kutusu, yönetilen özel durumlar veya yerel kod üzerinden geçen iş parçacıklarında yerel özel durumlar için işletim sistemi iletişim kutusunu preempts.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-132">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="c5d8b-133">İşlem her durumda sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-133">The process terminates in all cases.</span></span>

### <a name="migration"></a><span data-ttu-id="c5d8b-134">Geçiş</span><span class="sxs-lookup"><span data-stu-id="c5d8b-134">Migration</span></span>

<span data-ttu-id="c5d8b-135">.NET Framework 1,0 veya 1,1 ' den geçiş yapıyorsanız ve çalışma zamanı geri durağı avantajlarından yararlanarak, örneğin iş parçacıklarını sonlandırmak için aşağıdaki geçiş stratejilerinden birini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="c5d8b-135">If you are migrating from .NET Framework 1.0 or 1.1 and took advantage of the runtime backstop, for example to terminate threads, consider one of the following migration strategies:</span></span>  
  
- <span data-ttu-id="c5d8b-136">Bir sinyal alındığında iş parçacığının düzgün bir şekilde çıkış yapabilmesi için kodu yeniden yapılandır.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-136">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
- <span data-ttu-id="c5d8b-137"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>İş parçacığını durdurmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-137">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
- <span data-ttu-id="c5d8b-138">İşlem sonlandırmasının devam edebilmesi için bir iş parçacığının durdurulması gerekiyorsa, işlem çıkışında otomatik olarak sonlandırılmak için iş parçacığını bir arka plan iş parçacığı yapın.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-138">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
<span data-ttu-id="c5d8b-139">Her durumda, strateji özel durumlar için tasarım kılavuzunu izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-139">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="c5d8b-140">[Özel durumlar Için tasarım yönergelerine](../design-guidelines/exceptions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-140">See [Design Guidelines for Exceptions](../design-guidelines/exceptions.md).</span></span>  
  
<span data-ttu-id="c5d8b-141">Geçici bir uyumluluk ölçüsü olarak, Yöneticiler `<runtime>` uygulama yapılandırma dosyasının bölümüne bir uyumluluk bayrağı yerleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-141">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="c5d8b-142">Bu, ortak dil çalışma zamanının 1,0 ve 1,1 sürümlerinin davranışına dönüşmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-142">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="c5d8b-143">Konak geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="c5d8b-143">Host Override</span></span>

<span data-ttu-id="c5d8b-144">Yönetilmeyen bir konak, ortak dil çalışma zamanının varsayılan işlenmemiş özel durum ilkesini geçersiz kılmak için barındırma API 'sindeki [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabirimini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-144">An unmanaged host can use the [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="c5d8b-145">[ICLRPolicyManager:: SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) işlevi, işlenmemiş özel durumlar için ilkeyi ayarlamak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-145">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d8b-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5d8b-146">See also</span></span>

- [<span data-ttu-id="c5d8b-147">Yönetilen İş Parçacığı Oluşturma Temelleri</span><span class="sxs-lookup"><span data-stu-id="c5d8b-147">Managed Threading Basics</span></span>](managed-threading-basics.md)

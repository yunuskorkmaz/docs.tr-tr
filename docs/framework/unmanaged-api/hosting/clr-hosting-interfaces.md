---
description: 'Daha fazla bilgi edinin: CLR barındırma arabirimleri'
title: CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: f42a74698607ffbed4a981f061d13ea4e9d634d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799908"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="0270d-103">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0270d-103">CLR Hosting Interfaces</span></span>

<span data-ttu-id="0270d-104">Bu bölümde, yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) uygulamalarıyla tümleştirmeleri için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0270d-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="0270d-105">Bilgiler .NET Framework sürüm 2,0 ve sonraki sürümlere aittir.</span><span class="sxs-lookup"><span data-stu-id="0270d-105">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="0270d-106">Bu arabirimler konağın, çalışma zamanının daha birçok yönünü 1,0 ve 1,1 sürümlerinde mümkün olandan çok daha fazla denetlemesine olanak tanır ve CLR ile konağın yürütme modeli arasında çok daha sıkı bir tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-106">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="0270d-107">.NET Framework sürüm 1,0 ve 1,1 ' de barındırma modeli, CLR 'yi bir işleme yüklemek, belirli ayarları yapılandırmak ve olay bildirimleri almak için yönetilmeyen bir konağı etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="0270d-107">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="0270d-108">Ancak, genel olarak, ana bilgisayar ve CLR bu işlemde bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="0270d-108">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="0270d-109">.NET Framework sürüm 2,0 ve sonraki sürümlerinde, yeni soyutlama katmanları konağın Win32 derlemesinde bulunan türler tarafından şu anda sağlanmış birçok kaynağı sağlamasına ve konağın yapılandırabilmesinin bir dizi özelliği genişletmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="0270d-109">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0270d-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0270d-110">In This Section</span></span>  

 [<span data-ttu-id="0270d-111">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-111">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="0270d-112">Kayıtlı bir olay için geri çağırma gerçekleştiren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-112">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="0270d-113">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-113">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="0270d-114">Bir grup içinde geri çağırma yapmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-114">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="0270d-115">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-115">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="0270d-116">Çalışma zamanı yapılandırmasını ayarlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-116">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="0270d-117">ICatalogServices Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-117">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="0270d-118">Hizmet kataloğu için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-118">Provides methods for cataloging services.</span></span> <span data-ttu-id="0270d-119">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="0270d-119">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="0270d-120">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-120">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="0270d-121">Konak ve derlemeler hakkında CLR arasındaki iletişimi destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-121">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="0270d-122">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-122">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="0270d-123">Konak tarafından değil, CLR tarafından yüklenen derlemelerin listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="0270d-123">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="0270d-124">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-124">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="0270d-125">Konağın, CLR 'nin çeşitli yönlerini uygulamasına erişmesi ve bunları yapılandırması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-125">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="0270d-126">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-126">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="0270d-127">Bir ana bilgisayarın bir dizi görevi bir tanımlayıcıyla ve kolay bir adla ilişkilendirilmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-127">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="0270d-128">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-128">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="0270d-129">Ana bilgisayarın hata raporlama için özel yığın dökümleri yapılandırmasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-129">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="0270d-130">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-130">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="0270d-131">Bir konağın, CLR 'nin çöp toplama sistemiyle etkileşimini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-131">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="0270d-132">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-132">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="0270d-133">Ana bilgisayarın derlemelerin ilke bilgilerinde yapılan değişiklikleri değerlendirmesi ve iletişim kurması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-133">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="0270d-134">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-134">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="0270d-135">Ana bilgisayarın, kısmen güvenilen kodda çalışan belirli yönetilen sınıfları, yöntemleri, özellikleri ve alanları engellemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-135">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="0270d-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="0270d-137">Konağın belirtilen g/ç isteklerinin durum CLR 'ye bildirmesini sağlayan bir geri çağırma yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="0270d-137">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="0270d-138">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-138">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="0270d-139">Konağın, Win32 fonksiyonuyla benzer bir yaklaşım kullanarak bellek baskısı koşullarını rapor etmesini sağlar `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="0270d-139">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="0270d-140">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-140">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="0270d-141">Konağın CLR olayları için geri çağırmaları kaydetmesini ve kaydını iptal etme olanağı sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-141">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="0270d-142">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-142">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="0270d-143">, Ana bilgisayarın hata ve zaman aşımları durumunda gerçekleştirilecek ilke eylemlerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-143">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="0270d-144">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-144">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="0270d-145">, Bu kimliği oluşturmaya veya anlamaya gerek kalmadan derlemenin CLR 'nin kimlik bilgilerini kullanarak bir derlemenin yoklama kimliklerini almasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-145">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="0270d-146">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-146">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="0270d-147">Bu kimlikleri oluşturmaya veya anlamaya gerek kalmadan, konağın, CLR 'ye yönelik derleme kimliği verilerini kullanarak bir dosya veya akış tarafından başvurulan derlemelerin kümesini işlemesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-147">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="0270d-148">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-148">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="0270d-149">Konak denetim arabirimini ayarlamaya yönelik ek bir yöntem ile [ICorRuntimeHost](icorruntimehost-interface.md)'a benzer yetenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-149">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="0270d-150">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-150">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="0270d-151">, İstenen görevlerle ilgili bilgi almak ve eşitleme uygulamasında kilitlenmeleri algılamak için ana bilgisayar için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-151">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="0270d-152">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-152">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="0270d-153">Konağın CLR istekleri yapmasını veya ilişkili görevle ilgili olarak CLR 'ye bildirim sağlamasını etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-153">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="0270d-154">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-154">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="0270d-155">, CLR 'nin doğrudan CLR 'nin yeni bir görev oluşturmasını, şu anda yürütülmekte olan görevi almasını ve görevin coğrafi dilini ve kültürünü ayarlamanızı sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-155">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="0270d-156">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-156">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="0270d-157">Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-157">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="0270d-158">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-158">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="0270d-159">CLR yapılandırması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-159">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="0270d-160">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-160">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="0270d-161">İş parçacığı havuzuna erişim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-161">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="0270d-162">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-162">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="0270d-163">Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-163">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="0270d-164">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-164">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="0270d-165">, Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesi ve engellemesini kaldırma hakkında bilgi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-165">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="0270d-166">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-166">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="0270d-167">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-167">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="0270d-168">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-168">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="0270d-169">, Bir konağın çöp toplama segmentinin boyutunu ve çöp toplama sisteminin en büyük boyutunu ' dan büyük değerlere ayarlamaya olanak sağlayan [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini sağlar `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="0270d-169">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="0270d-170">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-170">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="0270d-171">Çöp toplayıcısının sanal bellek sınırlarını değiştirmesini istemek için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-171">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="0270d-172">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-172">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="0270d-173">Çöp toplama için engellenebilecek iş parçacıklarının zamanlamaya katılmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-173">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="0270d-174">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-174">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="0270d-175">Bir konağın CLR veya konak tarafından yüklenmesi gereken derleme kümelerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-175">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="0270d-176">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-176">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="0270d-177">Bir konağın CLR 'den bağımsız olarak derlemeleri ve modülleri yüklemesine imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-177">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="0270d-178">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-178">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="0270d-179">Ana bilgisayar tarafından uygulanan otomatik sıfırlama olayının gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-179">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="0270d-180">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-180">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="0270d-181">Derlemelerin yüklenmesini yapılandırmak için ve konağın desteklediği barındırma arabirimlerini belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-181">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="0270d-182">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-182">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="0270d-183">İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="0270d-183">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="0270d-184">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-184">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="0270d-185">CLR tarafından uygulanan çöp toplama mekanizmasında olay konağını bildiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-185">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="0270d-186">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-186">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="0270d-187">CLR 'nin konak tarafından sağlanan g/ç tamamlama bağlantı noktalarıyla etkileşime geçmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-187">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="0270d-188">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-188">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="0270d-189">CLR 'nin, ana bilgisayar aracılığıyla yığından hassas ayırmalar istemesi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-189">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="0270d-190">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-190">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="0270d-191">Konağın el ile sıfırlama olayının temsili için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-191">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="0270d-192">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-192">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="0270d-193">Standart Win32 sanal bellek işlevlerini kullanmak yerine, CLR 'nin konak üzerinden sanal bellek istekleri yapması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-193">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="0270d-194">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-194">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="0270d-195">İptal, zaman aşımları veya hatalara karşı, CLR tarafından gerçekleştirilen eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-195">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="0270d-196">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-196">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="0270d-197">CLR 'nin konak tarafından uygulanan güvenlik bağlamı bilgilerini korumasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-197">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="0270d-198">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-198">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="0270d-199">, Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamını ve üzerinde erişimi etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-199">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="0270d-200">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-200">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="0270d-201">Ana bilgisayar tarafından uygulanan semaforun bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-201">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="0270d-202">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-202">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="0270d-203">, Win32 eşitleme işlevlerini kullanmak yerine, Konağı çağırarak eşitleme temelleri oluşturmak için CLR için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-203">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="0270d-204">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-204">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="0270d-205">, CLR 'nin görevleri yönetmek üzere konakla iletişim kurmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-205">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="0270d-206">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-206">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="0270d-207">CLR 'nin standart işletim sistemi iş parçacığı veya fiber işlevlerini kullanmak yerine ana bilgisayar aracılığıyla görevlerle çalışmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-207">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="0270d-208">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-208">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="0270d-209">CLR için iş öğelerini yapılandırmak ve iş öğelerini iş parçacığı havuzuna sıraya almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-209">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="0270d-210">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-210">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="0270d-211">Yönetilen bir nesneyi denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-211">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="0270d-212">IObjectHandle</span><span class="sxs-lookup"><span data-stu-id="0270d-212">"IObjectHandle"</span></span>  
 <span data-ttu-id="0270d-213">Değer temelli nesneleri yöneltme 'dan sarmalama için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-213">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="0270d-214">ITypeName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-214">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="0270d-215">Tür adı bilgilerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-215">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="0270d-216">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="0270d-216">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="0270d-217">ITypeNameBuilder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-217">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="0270d-218">Bir tür adı oluşturmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-218">Provides methods for building a type name.</span></span> <span data-ttu-id="0270d-219">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="0270d-219">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="0270d-220">ITypeNameFactory Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0270d-220">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="0270d-221">Bir tür adının çıkarılması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-221">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="0270d-222">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="0270d-222">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="0270d-223">IValidator</span><span class="sxs-lookup"><span data-stu-id="0270d-223">"IValidator"</span></span>  
 <span data-ttu-id="0270d-224">Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0270d-224">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0270d-225">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0270d-225">Related Sections</span></span>  

 [<span data-ttu-id="0270d-226">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="0270d-226">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="0270d-227">.NET Framework sürüm 1,0 ve 1,1 ' de sunulan barındırma arabirimlerini tanımlayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="0270d-227">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="0270d-228">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0270d-228">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="0270d-229">.NET Framework 4 ' te belirtilen barındırma arabirimlerini tanımlayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="0270d-229">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>

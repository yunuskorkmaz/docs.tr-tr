---
title: CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 77f2ba64d9bdbe9793d56e88dae46fd506119ab8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719053"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="00140-102">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00140-102">CLR Hosting Interfaces</span></span>

<span data-ttu-id="00140-103">Bu bölümde, yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) uygulamalarıyla tümleştirmeleri için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00140-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="00140-104">Bilgiler .NET Framework sürüm 2,0 ve sonraki sürümlere aittir.</span><span class="sxs-lookup"><span data-stu-id="00140-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="00140-105">Bu arabirimler konağın, çalışma zamanının daha birçok yönünü 1,0 ve 1,1 sürümlerinde mümkün olandan çok daha fazla denetlemesine olanak tanır ve CLR ile konağın yürütme modeli arasında çok daha sıkı bir tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="00140-106">.NET Framework sürüm 1,0 ve 1,1 ' de barındırma modeli, CLR 'yi bir işleme yüklemek, belirli ayarları yapılandırmak ve olay bildirimleri almak için yönetilmeyen bir konağı etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="00140-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="00140-107">Ancak, genel olarak, ana bilgisayar ve CLR bu işlemde bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="00140-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="00140-108">.NET Framework sürüm 2,0 ve sonraki sürümlerinde, yeni soyutlama katmanları konağın Win32 derlemesinde bulunan türler tarafından şu anda sağlanmış birçok kaynağı sağlamasına ve konağın yapılandırabilmesinin bir dizi özelliği genişletmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="00140-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00140-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="00140-109">In This Section</span></span>  

 [<span data-ttu-id="00140-110">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-110">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="00140-111">Kayıtlı bir olay için geri çağırma gerçekleştiren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="00140-112">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-112">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="00140-113">Bir grup içinde geri çağırma yapmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="00140-114">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="00140-115">Çalışma zamanı yapılandırmasını ayarlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="00140-116">ICatalogServices Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-116">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="00140-117">Hizmet kataloğu için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="00140-118">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="00140-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="00140-119">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="00140-120">Konak ve derlemeler hakkında CLR arasındaki iletişimi destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="00140-121">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="00140-122">Konak tarafından değil, CLR tarafından yüklenen derlemelerin listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="00140-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="00140-123">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="00140-124">Konağın, CLR 'nin çeşitli yönlerini uygulamasına erişmesi ve bunları yapılandırması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="00140-125">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="00140-126">Bir ana bilgisayarın bir dizi görevi bir tanımlayıcıyla ve kolay bir adla ilişkilendirilmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="00140-127">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-127">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="00140-128">Ana bilgisayarın hata raporlama için özel yığın dökümleri yapılandırmasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="00140-129">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-129">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="00140-130">Bir konağın, CLR 'nin çöp toplama sistemiyle etkileşimini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="00140-131">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-131">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="00140-132">Ana bilgisayarın derlemelerin ilke bilgilerinde yapılan değişiklikleri değerlendirmesi ve iletişim kurması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="00140-133">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-133">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="00140-134">Ana bilgisayarın, kısmen güvenilen kodda çalışan belirli yönetilen sınıfları, yöntemleri, özellikleri ve alanları engellemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="00140-135">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="00140-136">Konağın belirtilen g/ç isteklerinin durum CLR 'ye bildirmesini sağlayan bir geri çağırma yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="00140-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="00140-137">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="00140-138">Konağın, Win32 fonksiyonuyla benzer bir yaklaşım kullanarak bellek baskısı koşullarını rapor etmesini sağlar `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="00140-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="00140-139">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-139">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="00140-140">Konağın CLR olayları için geri çağırmaları kaydetmesini ve kaydını iptal etme olanağı sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="00140-141">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="00140-142">, Ana bilgisayarın hata ve zaman aşımları durumunda gerçekleştirilecek ilke eylemlerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="00140-143">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="00140-144">, Bu kimliği oluşturmaya veya anlamaya gerek kalmadan derlemenin CLR 'nin kimlik bilgilerini kullanarak bir derlemenin yoklama kimliklerini almasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="00140-145">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-145">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="00140-146">Bu kimlikleri oluşturmaya veya anlamaya gerek kalmadan, konağın, CLR 'ye yönelik derleme kimliği verilerini kullanarak bir dosya veya akış tarafından başvurulan derlemelerin kümesini işlemesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="00140-147">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-147">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="00140-148">Konak denetim arabirimini ayarlamaya yönelik ek bir yöntem ile [ICorRuntimeHost](icorruntimehost-interface.md)'a benzer yetenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-148">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="00140-149">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-149">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="00140-150">, İstenen görevlerle ilgili bilgi almak ve eşitleme uygulamasında kilitlenmeleri algılamak için ana bilgisayar için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="00140-151">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-151">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="00140-152">Konağın CLR istekleri yapmasını veya ilişkili görevle ilgili olarak CLR 'ye bildirim sağlamasını etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="00140-153">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="00140-154">, CLR 'nin doğrudan CLR 'nin yeni bir görev oluşturmasını, şu anda yürütülmekte olan görevi almasını ve görevin coğrafi dilini ve kültürünü ayarlamanızı sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="00140-155">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-155">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="00140-156">Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="00140-157">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-157">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="00140-158">CLR yapılandırması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="00140-159">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-159">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="00140-160">İş parçacığı havuzuna erişim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="00140-161">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-161">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="00140-162">Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="00140-163">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-163">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="00140-164">, Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesi ve engellemesini kaldırma hakkında bilgi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="00140-165">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-165">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="00140-166">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="00140-167">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-167">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="00140-168">, Bir konağın çöp toplama segmentinin boyutunu ve çöp toplama sisteminin en büyük boyutunu ' dan büyük değerlere ayarlamaya olanak sağlayan [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini sağlar `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="00140-168">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="00140-169">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-169">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="00140-170">Çöp toplayıcısının sanal bellek sınırlarını değiştirmesini istemek için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="00140-171">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-171">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="00140-172">Çöp toplama için engellenebilecek iş parçacıklarının zamanlamaya katılmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="00140-173">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-173">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="00140-174">Bir konağın CLR veya konak tarafından yüklenmesi gereken derleme kümelerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="00140-175">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-175">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="00140-176">Bir konağın CLR 'den bağımsız olarak derlemeleri ve modülleri yüklemesine imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="00140-177">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-177">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="00140-178">Ana bilgisayar tarafından uygulanan otomatik sıfırlama olayının gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="00140-179">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-179">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="00140-180">Derlemelerin yüklenmesini yapılandırmak için ve konağın desteklediği barındırma arabirimlerini belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="00140-181">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-181">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="00140-182">İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="00140-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="00140-183">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-183">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="00140-184">CLR tarafından uygulanan çöp toplama mekanizmasında olay konağını bildiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="00140-185">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-185">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="00140-186">CLR 'nin konak tarafından sağlanan g/ç tamamlama bağlantı noktalarıyla etkileşime geçmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="00140-187">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-187">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="00140-188">CLR 'nin, ana bilgisayar aracılığıyla yığından hassas ayırmalar istemesi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="00140-189">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-189">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="00140-190">Konağın el ile sıfırlama olayının temsili için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="00140-191">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-191">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="00140-192">Standart Win32 sanal bellek işlevlerini kullanmak yerine, CLR 'nin konak üzerinden sanal bellek istekleri yapması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="00140-193">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-193">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="00140-194">İptal, zaman aşımları veya hatalara karşı, CLR tarafından gerçekleştirilen eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="00140-195">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-195">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="00140-196">CLR 'nin konak tarafından uygulanan güvenlik bağlamı bilgilerini korumasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="00140-197">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-197">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="00140-198">, Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamını ve üzerinde erişimi etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="00140-199">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-199">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="00140-200">Ana bilgisayar tarafından uygulanan semaforun bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="00140-201">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-201">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="00140-202">, Win32 eşitleme işlevlerini kullanmak yerine, Konağı çağırarak eşitleme temelleri oluşturmak için CLR için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="00140-203">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-203">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="00140-204">, CLR 'nin görevleri yönetmek üzere konakla iletişim kurmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="00140-205">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-205">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="00140-206">CLR 'nin standart işletim sistemi iş parçacığı veya fiber işlevlerini kullanmak yerine ana bilgisayar aracılığıyla görevlerle çalışmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="00140-207">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-207">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="00140-208">CLR için iş öğelerini yapılandırmak ve iş öğelerini iş parçacığı havuzuna sıraya almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="00140-209">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-209">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="00140-210">Yönetilen bir nesneyi denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="00140-211">IObjectHandle</span><span class="sxs-lookup"><span data-stu-id="00140-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="00140-212">Değer temelli nesneleri yöneltme 'dan sarmalama için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="00140-213">ITypeName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-213">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="00140-214">Tür adı bilgilerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="00140-215">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="00140-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="00140-216">ITypeNameBuilder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-216">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="00140-217">Bir tür adı oluşturmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-217">Provides methods for building a type name.</span></span> <span data-ttu-id="00140-218">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="00140-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="00140-219">ITypeNameFactory Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00140-219">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="00140-220">Bir tür adının çıkarılması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="00140-221">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="00140-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="00140-222">IValidator</span><span class="sxs-lookup"><span data-stu-id="00140-222">"IValidator"</span></span>  
 <span data-ttu-id="00140-223">Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00140-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="00140-224">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="00140-224">Related Sections</span></span>  

 [<span data-ttu-id="00140-225">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="00140-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="00140-226">.NET Framework sürüm 1,0 ve 1,1 ' de sunulan barındırma arabirimlerini tanımlayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="00140-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="00140-227">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00140-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="00140-228">.NET Framework 4 ' te belirtilen barındırma arabirimlerini tanımlayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="00140-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>

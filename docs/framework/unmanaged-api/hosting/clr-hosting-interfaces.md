---
title: CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 66fdd97d101f5ea53a96b996a2a60e5ed65a2701
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131962"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="e95bd-102">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e95bd-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="e95bd-103">Bu bölümde, yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) uygulamalarıyla tümleştirmeleri için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e95bd-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="e95bd-104">Bilgiler .NET Framework sürüm 2,0 ve sonraki sürümlere aittir.</span><span class="sxs-lookup"><span data-stu-id="e95bd-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="e95bd-105">Bu arabirimler konağın, çalışma zamanının daha birçok yönünü 1,0 ve 1,1 sürümlerinde mümkün olandan çok daha fazla denetlemesine olanak tanır ve CLR ile konağın yürütme modeli arasında çok daha sıkı bir tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="e95bd-106">.NET Framework sürüm 1,0 ve 1,1 ' de barındırma modeli, CLR 'yi bir işleme yüklemek, belirli ayarları yapılandırmak ve olay bildirimleri almak için yönetilmeyen bir konağı etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="e95bd-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="e95bd-107">Ancak, genel olarak, ana bilgisayar ve CLR bu işlemde bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e95bd-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="e95bd-108">.NET Framework sürüm 2,0 ve sonraki sürümlerinde, yeni soyutlama katmanları konağın Win32 derlemesinde bulunan türler tarafından şu anda sağlanmış birçok kaynağı sağlamasına ve konağın yapılandırabilmesinin bir dizi özelliği genişletmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e95bd-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e95bd-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e95bd-109">In This Section</span></span>  
 [<span data-ttu-id="e95bd-110">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="e95bd-111">Kayıtlı bir olay için geri çağırma gerçekleştiren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="e95bd-112">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="e95bd-113">Bir grup içinde geri çağırma yapmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="e95bd-114">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="e95bd-115">Çalışma zamanı yapılandırmasını ayarlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="e95bd-116">ICatalogServices Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="e95bd-117">Hizmet kataloğu için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="e95bd-118">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="e95bd-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="e95bd-119">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="e95bd-120">Konak ve derlemeler hakkında CLR arasındaki iletişimi destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="e95bd-121">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="e95bd-122">Konak tarafından değil, CLR tarafından yüklenen derlemelerin listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="e95bd-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="e95bd-123">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="e95bd-124">Konağın, CLR 'nin çeşitli yönlerini uygulamasına erişmesi ve bunları yapılandırması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="e95bd-125">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="e95bd-126">Bir ana bilgisayarın bir dizi görevi bir tanımlayıcıyla ve kolay bir adla ilişkilendirilmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="e95bd-127">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="e95bd-128">Ana bilgisayarın hata raporlama için özel yığın dökümleri yapılandırmasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="e95bd-129">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="e95bd-130">Bir konağın, CLR 'nin çöp toplama sistemiyle etkileşimini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="e95bd-131">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="e95bd-132">Ana bilgisayarın derlemelerin ilke bilgilerinde yapılan değişiklikleri değerlendirmesi ve iletişim kurması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="e95bd-133">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="e95bd-134">Ana bilgisayarın, kısmen güvenilen kodda çalışan belirli yönetilen sınıfları, yöntemleri, özellikleri ve alanları engellemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="e95bd-135">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="e95bd-136">Konağın belirtilen g/ç isteklerinin durum CLR 'ye bildirmesini sağlayan bir geri çağırma yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="e95bd-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="e95bd-137">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="e95bd-138">, Win32 `CreateMemoryResourceNotification` işlevinin benzeri bir yaklaşımı kullanarak bellek baskısı koşullarını raporlamak için ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="e95bd-139">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="e95bd-140">Konağın CLR olayları için geri çağırmaları kaydetmesini ve kaydını iptal etme olanağı sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="e95bd-141">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="e95bd-142">, Ana bilgisayarın hata ve zaman aşımları durumunda gerçekleştirilecek ilke eylemlerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="e95bd-143">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="e95bd-144">, Bu kimliği oluşturmaya veya anlamaya gerek kalmadan derlemenin CLR 'nin kimlik bilgilerini kullanarak bir derlemenin yoklama kimliklerini almasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="e95bd-145">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="e95bd-146">Bu kimlikleri oluşturmaya veya anlamaya gerek kalmadan, konağın, CLR 'ye yönelik derleme kimliği verilerini kullanarak bir dosya veya akış tarafından başvurulan derlemelerin kümesini işlemesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="e95bd-147">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="e95bd-148">Konak denetim arabirimini ayarlamaya yönelik ek bir yöntem ile [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)'a benzer yetenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="e95bd-149">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="e95bd-150">, İstenen görevlerle ilgili bilgi almak ve eşitleme uygulamasında kilitlenmeleri algılamak için ana bilgisayar için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="e95bd-151">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="e95bd-152">Konağın CLR istekleri yapmasını veya ilişkili görevle ilgili olarak CLR 'ye bildirim sağlamasını etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="e95bd-153">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="e95bd-154">, CLR 'nin doğrudan CLR 'nin yeni bir görev oluşturmasını, şu anda yürütülmekte olan görevi almasını ve görevin coğrafi dilini ve kültürünü ayarlamanızı sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="e95bd-155">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="e95bd-156">Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="e95bd-157">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="e95bd-158">CLR yapılandırması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="e95bd-159">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="e95bd-160">İş parçacığı havuzuna erişim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="e95bd-161">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="e95bd-162">Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="e95bd-163">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="e95bd-164">, Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesi ve engellemesini kaldırma hakkında bilgi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="e95bd-165">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="e95bd-166">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="e95bd-167">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="e95bd-168">Bir konağın çöp toplama kesiminin boyutunu ve çöp toplama sisteminin en büyük boyutunu `DWORD`' den büyük değerlere ayarlamaya olanak tanıyan [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="e95bd-169">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="e95bd-170">Çöp toplayıcısının sanal bellek sınırlarını değiştirmesini istemek için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="e95bd-171">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="e95bd-172">Çöp toplama için engellenebilecek iş parçacıklarının zamanlamaya katılmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="e95bd-173">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="e95bd-174">Bir konağın CLR veya konak tarafından yüklenmesi gereken derleme kümelerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="e95bd-175">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="e95bd-176">Bir konağın CLR 'den bağımsız olarak derlemeleri ve modülleri yüklemesine imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="e95bd-177">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="e95bd-178">Ana bilgisayar tarafından uygulanan otomatik sıfırlama olayının gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="e95bd-179">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="e95bd-180">Derlemelerin yüklenmesini yapılandırmak için ve konağın desteklediği barındırma arabirimlerini belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="e95bd-181">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="e95bd-182">İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="e95bd-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="e95bd-183">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="e95bd-184">CLR tarafından uygulanan çöp toplama mekanizmasında olay konağını bildiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="e95bd-185">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="e95bd-186">CLR 'nin konak tarafından sağlanan g/ç tamamlama bağlantı noktalarıyla etkileşime geçmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="e95bd-187">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="e95bd-188">CLR 'nin, ana bilgisayar aracılığıyla yığından hassas ayırmalar istemesi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="e95bd-189">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="e95bd-190">Konağın el ile sıfırlama olayının temsili için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="e95bd-191">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="e95bd-192">Standart Win32 sanal bellek işlevlerini kullanmak yerine, CLR 'nin konak üzerinden sanal bellek istekleri yapması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="e95bd-193">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="e95bd-194">İptal, zaman aşımları veya hatalara karşı, CLR tarafından gerçekleştirilen eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="e95bd-195">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="e95bd-196">CLR 'nin konak tarafından uygulanan güvenlik bağlamı bilgilerini korumasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="e95bd-197">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="e95bd-198">, Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamını ve üzerinde erişimi etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="e95bd-199">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="e95bd-200">Ana bilgisayar tarafından uygulanan semaforun bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="e95bd-201">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="e95bd-202">, Win32 eşitleme işlevlerini kullanmak yerine, Konağı çağırarak eşitleme temelleri oluşturmak için CLR için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="e95bd-203">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="e95bd-204">, CLR 'nin görevleri yönetmek üzere konakla iletişim kurmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="e95bd-205">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="e95bd-206">CLR 'nin standart işletim sistemi iş parçacığı veya fiber işlevlerini kullanmak yerine ana bilgisayar aracılığıyla görevlerle çalışmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="e95bd-207">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="e95bd-208">CLR için iş öğelerini yapılandırmak ve iş öğelerini iş parçacığı havuzuna sıraya almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="e95bd-209">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="e95bd-210">Yönetilen bir nesneyi denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="e95bd-211">IObjectHandle</span><span class="sxs-lookup"><span data-stu-id="e95bd-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="e95bd-212">Değer temelli nesneleri yöneltme 'dan sarmalama için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="e95bd-213">ITypeName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="e95bd-214">Tür adı bilgilerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="e95bd-215">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="e95bd-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="e95bd-216">ITypeNameBuilder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="e95bd-217">Bir tür adı oluşturmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-217">Provides methods for building a type name.</span></span> <span data-ttu-id="e95bd-218">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="e95bd-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="e95bd-219">ITypeNameFactory Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95bd-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="e95bd-220">Bir tür adının çıkarılması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="e95bd-221">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="e95bd-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="e95bd-222">IValidator</span><span class="sxs-lookup"><span data-stu-id="e95bd-222">"IValidator"</span></span>  
 <span data-ttu-id="e95bd-223">Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bd-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e95bd-224">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e95bd-224">Related Sections</span></span>  
 [<span data-ttu-id="e95bd-225">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="e95bd-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="e95bd-226">.NET Framework sürüm 1,0 ve 1,1 ' de sunulan barındırma arabirimlerini tanımlayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="e95bd-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="e95bd-227">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e95bd-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="e95bd-228">.NET Framework 4 ' te belirtilen barındırma arabirimlerini tanımlayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="e95bd-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>

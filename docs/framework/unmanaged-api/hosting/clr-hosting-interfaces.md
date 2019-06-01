---
title: CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80404e65263aa4ad245a8c8213630a4736bd7b11
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456877"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="9e176-102">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e176-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="9e176-103">Bu bölümde, yönetilmeyen arabirimler açıklanmaktadır. konaklar, ortak dil çalışma zamanı (CLR) uygulamalarıyla tümleştirmeleri için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e176-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="9e176-104">Bilgiler .NET Framework sürüm 2.0 ve sonraki sürümler ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="9e176-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="9e176-105">Bu arabirimler, çalışma zamanı 1.0 ve 1.1 sürümlerinde mümkün olandan çok daha fazla yönlerini denetlemek konak etkinleştirmek ve kadar CLR ve ana bilgisayarın yürütme modeli arasında sıkı bir tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="9e176-106">.NET Framework 1.0 ve 1.1 sürümlerinde, barındırma modeli CLR'yi bir işleme, belirli ayarları yapılandırmak ve olay bildirimlerini almak üzere yüklemek yönetilmeyen bir konak etkin.</span><span class="sxs-lookup"><span data-stu-id="9e176-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="9e176-107">Ancak, genel olarak, konak ve CLR bağımsız olarak bu işlemde çalışan.</span><span class="sxs-lookup"><span data-stu-id="9e176-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="9e176-108">.NET Framework sürüm 2.0 ve sonraki sürümlerinde soyutlama yeni katmanları Win32 bütünleştirilmiş kodundaki türler tarafından şu anda sağlanan kaynak sağlayın ve konak yapılandırabileceğiniz özellikler kümesini genişletin konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e176-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9e176-109">In This Section</span></span>  
 [<span data-ttu-id="9e176-110">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="9e176-111">Kayıtlı bir olay için bir geri çağırma işlemini gerçekleştiren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="9e176-112">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="9e176-113">Bir grup içinde geri çağırmaları sağlama yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="9e176-114">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="9e176-115">Çalışma zamanı yapılandırma ayarlaması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="9e176-116">ICatalogServices Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="9e176-117">Hizmetleri kataloglama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="9e176-118">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="9e176-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="9e176-119">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="9e176-120">CLR derlemeleri hakkında ile konak arasındaki iletişimi desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="9e176-121">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="9e176-122">CLR tarafından ve konak tarafından yüklenen derlemelerin bir listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="9e176-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="9e176-123">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="9e176-124">Erişim ve çeşitli yönlerini, CLR yapılandırmak konak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="9e176-125">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="9e176-126">Bir görev kümesi bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek bir konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="9e176-127">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="9e176-128">Hata bildirimi için özel bir yığın dökümlerini yapılandırmak konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="9e176-129">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="9e176-130">CLR'nin çöp toplama sistemi ile etkileşim kurmak bir konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="9e176-131">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="9e176-132">Değerlendirmek ve ilke bilgilerini derlemeler için değişiklikleri iletişim kurmak ana bilgisayar için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="9e176-133">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="9e176-134">Yönetilen sınıflar, yöntemler, özellikler ve alanları kısmen güvenilen kod çalıştırılmasını engellemek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="9e176-135">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="9e176-136">CLR belirtilen g/ç istekleri durumunu bildirmek için ana sağlayan bir geri çağırma yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="9e176-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="9e176-137">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="9e176-138">Win32 için benzer bir yaklaşım kullanarak rapor bellek baskısı koşullarını sağlayan `CreateMemoryResourceNotification` işlevi.</span><span class="sxs-lookup"><span data-stu-id="9e176-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="9e176-139">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="9e176-140">Kaydolun ve CLR olayları için geri çağırmaları kaydını silmek konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="9e176-141">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="9e176-142">Hataları ve zaman aşımları durumunda uygulanacak ilke eylemleri belirtmek konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="9e176-143">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="9e176-144">CLR, iç oluşturmak veya kimliğe anlamanıza gerek kalmadan derlemenin kimlik bilgilerini kullanarak bir derleme araştırma kimliklerini almak konağı etkinleştirme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="9e176-145">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="9e176-146">Bir dosya veya akışı oluşturmak veya kimliklerle anlamanıza gerek kalmadan iç CLR için olan derleme kimlik verilerini kullanarak tarafından başvurulan derlemeler kümesini işlemek için ana olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="9e176-147">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="9e176-148">Benzer özellikleri sağlayan [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), ana bilgisayar denetimi arabirimi ayarlamak için ek bir yöntem ile.</span><span class="sxs-lookup"><span data-stu-id="9e176-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="9e176-149">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="9e176-150">İstenilen görevler hakkında bilgi almak ve kilitlenmeleri eşitleme uygulanması algılamak için konak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="9e176-151">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="9e176-152">CLR isteklerde veya CLR ilişkili görevle ilgili bildirim sağlamak için konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="9e176-153">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="9e176-154">CLR yeni bir görev oluşturma, şu anda yürütülmekte olan görevi Al ve coğrafi dil ve kültür görev için açıkça istemek üzere konağın olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="9e176-155">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="9e176-156">Taşınabilir yürütülebilir (PE) görüntüleri doğrulanıyor ve doğrulama hatalarını raporlama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="9e176-157">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="9e176-158">CLR yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="9e176-159">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="9e176-160">İş parçacığı havuzu erişmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="9e176-161">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="9e176-162">Hata Ayıklama Hizmetleri durumuyla ilgili bilgileri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="9e176-163">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="9e176-164">Engelleme hakkında konak bildiren ve hata ayıklama Hizmetleri tarafından iş parçacıklarının engellemesinin kaldırılması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="9e176-165">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="9e176-166">Çöp toplama işleminin bazı yönlerini denetleme ve çöp toplama sistemi hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="9e176-167">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="9e176-168">Sağlar [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yönteminin çöp toplama kesim boyutunu ve en büyük boyutu çöp toplama sistemin oluşturma sıfır değerleri büyük ayarlamak bir konak tanıyan `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="9e176-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="9e176-169">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="9e176-170">Çöp toplayıcı sanal bellek sınırlarını değiştirmek için ana istemek sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="9e176-171">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="9e176-172">Çöp toplama işlemi için normalde engellenecek iş parçacıklarını zamanlama katılım için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="9e176-173">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="9e176-174">Konak veya CLR tarafından yüklenmesi gereken derlemeler kümesini belirtmek bir konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="9e176-175">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="9e176-176">Derlemeler ve CLR bağımsız olarak modülleri yüklemek bir konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="9e176-177">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="9e176-178">Otomatik sıfırlama olaya ana bilgisayar tarafından uygulanan bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="9e176-179">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="9e176-180">Derlemeleri yüklenmesini yapılandırma ve ana bilgisayar destekler hangi barındırma arabirimleri belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="9e176-181">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="9e176-182">İş parçacığı için kritik bir bölüm konağın gösterimi işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="9e176-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="9e176-183">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="9e176-184">CLR tarafından uygulanan çöp toplama mekanizması olayların ana bilgisayara bildirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="9e176-185">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="9e176-186">Ana bilgisayar tarafından sağlanan g/ç tamamlama bağlantı noktaları ile etkileşim kurmak CLR olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="9e176-187">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="9e176-188">CLR'nin yığın konağı üzerinden hassas ayırmaları istek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="9e176-189">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="9e176-190">Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="9e176-191">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="9e176-192">Standart Win32 sanal bellek işlevleri kullanmak yerine ana bilgisayar üzerinden sanal bellek isteğinde bulunmak CLR için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="9e176-193">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="9e176-194">Ana bilgisayarının durumunda, CLR gerçekleştirdiği işlemleri durdurur, zaman aşımı veya hataları bildirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="9e176-195">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="9e176-196">Ana bilgisayar tarafından uygulanan güvenlik bağlamını korumak CLR sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="9e176-197">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="9e176-198">Erişimi etkinleştir ve şu anda çalışan bir iş parçacığı üzerinde güvenlik bağlamını denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="9e176-199">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="9e176-200">Ana bilgisayar tarafından uygulanan semafor bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="9e176-201">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="9e176-202">Eşitleme temellerine Win32 eşitleme işlevleri kullanmak yerine konak çağırarak oluşturmak CLR için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="9e176-203">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="9e176-204">Görevleri yönetmek üzere konaklarla iletişim kurmak CLR olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="9e176-205">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="9e176-206">Görevleri için standart işletim sistemi iş parçacığı veya fiber işlevlerini yerine ana bilgisayar üzerinden çalışmak CLR olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="9e176-207">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="9e176-208">CLR iş parçacığı havuzu yapılandırmak ve iş parçacığı havuzu iş öğelerine sıraya almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="9e176-209">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="9e176-210">Yönetilen bir nesnenin denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="9e176-211">"IObjectHandle"</span><span class="sxs-lookup"><span data-stu-id="9e176-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="9e176-212">Yöneltme açma değere göre sıralama nesneler için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="9e176-213">ITypeName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="9e176-214">Tür adı bilgileri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="9e176-215">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="9e176-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="9e176-216">ITypeNameBuilder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="9e176-217">Bir tür adı oluşturmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-217">Provides methods for building a type name.</span></span> <span data-ttu-id="9e176-218">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="9e176-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="9e176-219">ITypeNameFactory Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e176-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="9e176-220">Bir tür adı ayrıştırma için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="9e176-221">(Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="9e176-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="9e176-222">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="9e176-222">"IValidator"</span></span>  
 <span data-ttu-id="9e176-223">Taşınabilir yürütülebilir (PE) görüntüleri doğrulanıyor ve doğrulama hatalarını raporlama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e176-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9e176-224">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9e176-224">Related Sections</span></span>  
 [<span data-ttu-id="9e176-225">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="9e176-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="9e176-226">.NET Framework sürüm 1.0 ve 1.1 barındırma arabirimlerini açıklayan konulara içerir.</span><span class="sxs-lookup"><span data-stu-id="9e176-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="9e176-227">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e176-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="9e176-228">.NET Framework 4'te sağlanan barındırma arabirimleri açıklayan konulara içerir.</span><span class="sxs-lookup"><span data-stu-id="9e176-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>

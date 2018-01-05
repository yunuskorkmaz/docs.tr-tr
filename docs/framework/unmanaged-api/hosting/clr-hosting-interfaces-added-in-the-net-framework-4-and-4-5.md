---
title: ".NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61231715a24978e7fe57b2c9e87e7968dc0fdbc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="ad5bb-102">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad5bb-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="ad5bb-103">Bu bölümde yönetilmeyen arabirimler açıklanmaktadır konakları ortak dil çalışma zamanı (CLR) içinde tümleştirmek için kullanabilir [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]ve sonraki sürümlerinde uygulamalarına.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], and later versions into their applications.</span></span> <span data-ttu-id="ad5bb-104">Bu arabirimleri yapılandırmak ve süreç içine çalışma zamanı yükleme bir konak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="ad5bb-105">İle başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], tüm barındırma arabirimleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ad5bb-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
-   <span data-ttu-id="ad5bb-106">Ömür yönetimini kullanın (`AddRef` ve `Release`), kapsülleme (örtük bağlamı) ve `QueryInterface` com gelen</span><span class="sxs-lookup"><span data-stu-id="ad5bb-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
-   <span data-ttu-id="ad5bb-107">COM türleri gibi var. kullanmayın `BSTR`, `SAFEARRAY`, veya `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
-   <span data-ttu-id="ad5bb-108">Hiçbir grup modelleri, toplama veya kayıt defteri etkinleştirme kullanan vardır [CoCreateInstance işlevi](http://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="ad5bb-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](http://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad5bb-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ad5bb-109">In This Section</span></span>  
 [<span data-ttu-id="ad5bb-110">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="ad5bb-111">Bir uygulama etki alanının bellek ve CPU kullanımını denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="ad5bb-112">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="ad5bb-113">Varsayılan uygulama etki alanı başlatın ve başlatma özelliklerini belirtmek için kullanılan uygulama etki alanı yöneticisi belirtmek ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="ad5bb-114">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="ad5bb-115">Sağlar [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) atık toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil değerlere büyük ayarlamak bir konak etkinleştirir yöntemi `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="ad5bb-116">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="ad5bb-117">CLR belirli bir sürümünü döndürür, tüm yüklü CLRs listesinde, tüm işlem çalışma zamanları listesinde, etkinleştirme arabirimini döndürür ve bir derlemeyi derlemek için kullanılan CLR sürümünü bulma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="ad5bb-118">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="ad5bb-119">Sağlar [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) bir CLR arabirim sağlayan yöntemine temel İlkesi ölçütlerini, yönetilen derleme, sürüm ve yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="ad5bb-120">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="ad5bb-121">Sürüm, dizin ve yük durumu da dahil olmak üzere belirli bir çalışma zamanı hakkında bilgi döndürmek yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="ad5bb-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="ad5bb-123">Derlemeleri tanımlayıcı adlar ile imzalama için temel genel statik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="ad5bb-124">Tüm [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) yöntemleri standart COM HRESULTs döndürür.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="ad5bb-125">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="ad5bb-126">Tanımlayıcı adlar SHA-2 grubunu güvenli karma algoritması (SHA-256, SHA-384 ve SHA-512) kullanarak oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="ad5bb-127">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad5bb-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="ad5bb-128">Tüm işlevselliğini sağlar [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Ayrıca, iş parçacığı iptalleri geçerli iş parçacığı üzerinde Gecikmeli için izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ad5bb-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ad5bb-129">Related Sections</span></span>  
 [<span data-ttu-id="ad5bb-130">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="ad5bb-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="ad5bb-131">.NET Framework sürüm 1.0 ve 1.1 ile sağlanan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="ad5bb-132">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad5bb-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="ad5bb-133">.NET Framework sürüm 2.0, 3.0 ve 3.5 ile sağlanan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="ad5bb-134">Barındırma</span><span class="sxs-lookup"><span data-stu-id="ad5bb-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="ad5bb-135">.NET Framework'te barındırma tanıtır.</span><span class="sxs-lookup"><span data-stu-id="ad5bb-135">Introduces hosting in the .NET Framework.</span></span>

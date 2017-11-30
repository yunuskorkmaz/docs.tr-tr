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
ms.openlocfilehash: 65d80734bfbe16c8b5052f8de1e4c6280b663707
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="2cd45-102">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2cd45-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="2cd45-103">Bu bölümde yönetilmeyen arabirimler açıklanmaktadır konakları ortak dil çalışma zamanı (CLR) içinde tümleştirmek için kullanabilir [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]ve sonraki sürümlerinde uygulamalarına.</span><span class="sxs-lookup"><span data-stu-id="2cd45-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], and later versions into their applications.</span></span> <span data-ttu-id="2cd45-104">Bu arabirimleri yapılandırmak ve süreç içine çalışma zamanı yükleme bir konak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="2cd45-105">İle başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], tüm barındırma arabirimleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2cd45-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
-   <span data-ttu-id="2cd45-106">Ömür yönetimini kullanın (`AddRef` ve `Release`), kapsülleme (örtük bağlamı) ve `QueryInterface` com gelen</span><span class="sxs-lookup"><span data-stu-id="2cd45-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
-   <span data-ttu-id="2cd45-107">COM türleri gibi var. kullanmayın `BSTR`, `SAFEARRAY`, veya `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="2cd45-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
-   <span data-ttu-id="2cd45-108">Hiçbir grup modelleri, toplama veya kayıt defteri etkinleştirme kullanan vardır [CoCreateInstance işlevi](http://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="2cd45-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](http://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2cd45-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2cd45-109">In This Section</span></span>  
 [<span data-ttu-id="2cd45-110">Iclrappdomainresourcemonitor arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="2cd45-111">Bir uygulama etki alanının bellek ve CPU kullanımını denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="2cd45-112">Iclrdomainmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="2cd45-113">Varsayılan uygulama etki alanı başlatın ve başlatma özelliklerini belirtmek için kullanılan uygulama etki alanı yöneticisi belirtmek ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="2cd45-114">Iclrgcmanager2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="2cd45-115">Sağlar [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) atık toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil değerlere büyük ayarlamak bir konak etkinleştirir yöntemi `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="2cd45-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="2cd45-116">Iclrmetahost arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="2cd45-117">CLR belirli bir sürümünü döndürür, tüm yüklü CLRs listesinde, tüm işlem çalışma zamanları listesinde, etkinleştirme arabirimini döndürür ve bir derlemeyi derlemek için kullanılan CLR sürümünü bulma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="2cd45-118">Iclrmetahostpolicy arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="2cd45-119">Sağlar [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) bir CLR arabirim sağlayan yöntemine temel İlkesi ölçütlerini, yönetilen derleme, sürüm ve yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="2cd45-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="2cd45-120">Iclrruntimeınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="2cd45-121">Sürüm, dizin ve yük durumu da dahil olmak üzere belirli bir çalışma zamanı hakkında bilgi döndürmek yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="2cd45-122">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="2cd45-123">Derlemeleri tanımlayıcı adlar ile imzalama için temel genel statik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="2cd45-124">Tüm [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) yöntemleri standart COM HRESULTs döndürür.</span><span class="sxs-lookup"><span data-stu-id="2cd45-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="2cd45-125">Iclrstrongname2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="2cd45-126">Tanımlayıcı adlar SHA-2 grubunu güvenli karma algoritması (SHA-256, SHA-384 ve SHA-512) kullanarak oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="2cd45-127">Iclrtask2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd45-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="2cd45-128">Tüm işlevselliğini sağlar [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Ayrıca, iş parçacığı iptalleri geçerli iş parçacığı üzerinde Gecikmeli için izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2cd45-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2cd45-129">Related Sections</span></span>  
 [<span data-ttu-id="2cd45-130">Kullanım dışı CLR barındırma arabirimleri ve coclass'ları</span><span class="sxs-lookup"><span data-stu-id="2cd45-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="2cd45-131">.NET Framework sürüm 1.0 ve 1.1 ile sağlanan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="2cd45-132">CLR barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2cd45-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="2cd45-133">.NET Framework sürüm 2.0, 3.0 ve 3.5 ile sağlanan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="2cd45-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="2cd45-134">Barındırma</span><span class="sxs-lookup"><span data-stu-id="2cd45-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="2cd45-135">.NET Framework'te barındırma tanıtır.</span><span class="sxs-lookup"><span data-stu-id="2cd45-135">Introduces hosting in the .NET Framework.</span></span>

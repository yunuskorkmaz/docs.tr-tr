---
title: .NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: aea88430d8f83234a1568bcaf433c2a75492e23a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195921"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="abc64-102">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="abc64-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="abc64-103">Bu bölümde, yönetilmeyen ana bilgisayarların .NET Framework 4, .NET Framework 4,5 ve sonraki sürümlerindeki ortak dil çalışma zamanını (CLR) bütünleştirmek için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="abc64-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="abc64-104">Bu arabirimler, bir ana bilgisayarın çalışma zamanını yapılandırmak ve bir işleme yüklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="abc64-105">.NET Framework 4 ' te başlayarak, tüm barındırma arabirimleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="abc64-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="abc64-106">Yaşam süresi yönetimi (`AddRef` ve `Release`), kapsülleme (örtük bağlam) ve COM 'dan `QueryInterface` kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="abc64-107">`BSTR`, `SAFEARRAY`veya `VARIANT`gibi COM türlerini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="abc64-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="abc64-108">[Cocreateınstance işlevini](https://go.microsoft.com/fwlink/?LinkId=142894)kullanan hiçbir Grup modeli, toplama veya kayıt defteri etkinleştirmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="abc64-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](https://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="abc64-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="abc64-109">In This Section</span></span>  
 [<span data-ttu-id="abc64-110">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="abc64-111">Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="abc64-112">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="abc64-113">Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="abc64-114">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="abc64-115">, Bir konağın çöp toplama kesiminin boyutunu ve çöp toplama sisteminin 1. kuşak en büyük boyutunu `DWORD`daha büyük değerlere ayarlayabilmesine olanak tanıyan [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="abc64-116">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="abc64-117">CLR 'nin belirli bir sürümünü döndüren, tüm yüklü CLRs 'leri listeleme, tüm işlem içi çalışma zamanlarını listeleme, etkinleştirme arabirimini geri döndürme ve bir derlemeyi derlemek için kullanılan CLR sürümünü bulma yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="abc64-118">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="abc64-119">İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan bir CLR arabirimi sağlayan [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="abc64-120">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="abc64-121">Sürüm, dizin ve yükleme durumu dahil olmak üzere belirli bir çalışma zamanı hakkında bilgi döndüren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="abc64-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="abc64-123">Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="abc64-124">Tüm [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) YÖNTEMLERI standart com HResults döndürür.</span><span class="sxs-lookup"><span data-stu-id="abc64-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="abc64-125">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="abc64-126">, SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="abc64-127">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc64-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="abc64-128">[ICLRTask arabiriminin](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc64-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="abc64-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="abc64-129">Related Sections</span></span>  
 [<span data-ttu-id="abc64-130">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="abc64-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="abc64-131">1,0 ve 1,1 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="abc64-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="abc64-132">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="abc64-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="abc64-133">2,0, 3,0 ve 3,5 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="abc64-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="abc64-134">Barındırma</span><span class="sxs-lookup"><span data-stu-id="abc64-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="abc64-135">.NET Framework barındırılmasını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="abc64-135">Introduces hosting in the .NET Framework.</span></span>

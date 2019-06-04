---
title: .NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89d71b3dfa71438b72fe622a491141364db25f52
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490661"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="4b502-102">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4b502-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="4b502-103">Bu bölümde, yönetilmeyen arabirimler açıklanmaktadır. konakları ortak dil çalışma zamanı (CLR) tümleştirme için kullanabileceğiniz bir .NET Framework 4, .NET Framework 4.5 ve sonraki sürümlerinde uygulamalarına.</span><span class="sxs-lookup"><span data-stu-id="4b502-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="4b502-104">Bu arabirimler, yapılandırmak ve çalışma zamanını bir işleme yüklemek bir konak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b502-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="4b502-105">Tüm barındırma arabirimleri, .NET Framework 4 ile başlayarak, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4b502-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="4b502-106">Ömür Yönetimi kullandıkları (`AddRef` ve `Release`), kapsülleme (örtük context) ve `QueryInterface` com gelen</span><span class="sxs-lookup"><span data-stu-id="4b502-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="4b502-107">COM türleri gibi var. kullanmayın `BSTR`, `SAFEARRAY`, veya `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="4b502-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="4b502-108">Apartman modeli, toplama, veya kayıt defteri etkinleştirme kullanan [CoCreateInstance işlevi](https://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="4b502-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](https://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b502-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4b502-109">In This Section</span></span>  
 [<span data-ttu-id="4b502-110">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="4b502-111">Bir uygulama etki alanının bellek ve CPU kullanımını denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b502-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="4b502-112">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="4b502-113">Varsayılan uygulama etki alanı başlatmak ve başlatma özelliklerini belirtmek için kullanılan uygulama etki alanı yöneticisi belirtmek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b502-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="4b502-114">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="4b502-115">Sağlar [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) çöp toplama kesim boyutunu ve en büyük boyutu çöp toplama sistemin nesil 0 değerine büyük ayarlamak bir konak sağlayan yöntemi `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="4b502-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="4b502-116">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="4b502-117">CLR'nin belirli bir sürümünü döndürmek, tüm yüklü CLRs listesinde, tüm işlem çalışma zamanları listesinde, etkinleştirme arabirimini döndürür ve bir derlemeyi derlemek için kullanılan CLR sürümü bulmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b502-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="4b502-118">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="4b502-119">Sağlar [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) CLR arabirimi sağlayan yöntemi temel İlkesi ölçütlerini, yönetilen bir derleme, sürüm ve yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="4b502-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="4b502-120">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="4b502-121">Sürüm, dizin ve yükleme durumu gibi belirli bir çalışma zamanı hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b502-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="4b502-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="4b502-123">Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b502-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="4b502-124">Tüm [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) yöntemleri standart COM HRESULTs döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b502-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="4b502-125">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="4b502-126">SHA-2 karma algoritma (SHA-256, SHA-384 ve SHA-512) güvenli kullanarak güçlü adlar oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b502-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="4b502-127">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b502-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="4b502-128">Tüm işlevlerini sağlar [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Ayrıca, iş parçacığı iptalleri geçerli iş parçacığında geciktirileceği izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b502-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4b502-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4b502-129">Related Sections</span></span>  
 [<span data-ttu-id="4b502-130">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="4b502-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="4b502-131">.NET Framework sürümleri 1.0 ve 1.1 ile sağlanan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b502-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="4b502-132">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4b502-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="4b502-133">.NET Framework sürüm 2.0, 3.0 ve 3.5 ile sağlanan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b502-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="4b502-134">Barındırma</span><span class="sxs-lookup"><span data-stu-id="4b502-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="4b502-135">.NET Framework barındırma tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4b502-135">Introduces hosting in the .NET Framework.</span></span>

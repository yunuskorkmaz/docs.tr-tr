---
description: "Hakkında daha fazla bilgi edinin: .NET Framework 4 ve 4,5 ' de eklenen CLR barındırma arabirimleri"
title: .NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: e7c5dd042822be8653d9c068e85a751aed622f06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799921"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="bc854-103">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bc854-103">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>

<span data-ttu-id="bc854-104">Bu bölümde, yönetilmeyen ana bilgisayarların .NET Framework 4, .NET Framework 4,5 ve sonraki sürümlerindeki ortak dil çalışma zamanını (CLR) bütünleştirmek için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc854-104">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="bc854-105">Bu arabirimler, bir ana bilgisayarın çalışma zamanını yapılandırmak ve bir işleme yüklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-105">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="bc854-106">.NET Framework 4 ' te başlayarak, tüm barındırma arabirimleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bc854-106">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="bc854-107">Yaşam süresi yönetimi ( `AddRef` ve `Release` ), kapsülleme (örtük bağlam) ve com ile kullanılır `QueryInterface` .</span><span class="sxs-lookup"><span data-stu-id="bc854-107">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="bc854-108">, Veya gibi COM türlerini kullanmaz `BSTR` `SAFEARRAY` `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="bc854-108">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="bc854-109">[Cocreateınstance işlevini](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)kullanan hiçbir Grup modeli, toplama veya kayıt defteri etkinleştirmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bc854-109">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc854-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bc854-110">In This Section</span></span>  

 [<span data-ttu-id="bc854-111">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-111">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="bc854-112">Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-112">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="bc854-113">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-113">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)  
 <span data-ttu-id="bc854-114">Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-114">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="bc854-115">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-115">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)  
 <span data-ttu-id="bc854-116">, Bir konağın çöp toplama segmentinin boyutunu ve çöp toplama sisteminin 1. kuşak en büyük boyut olan 0 ' dan büyük değerlere ayarlanmasını sağlayan [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini sağlar `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="bc854-116">Provides the [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="bc854-117">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)  
 <span data-ttu-id="bc854-118">CLR 'nin belirli bir sürümünü döndüren, tüm yüklü CLRs 'leri listeleme, tüm işlem içi çalışma zamanlarını listeleme, etkinleştirme arabirimini geri döndürme ve bir derlemeyi derlemek için kullanılan CLR sürümünü bulma yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-118">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="bc854-119">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-119">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="bc854-120">İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan bir CLR arabirimi sağlayan [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) metodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-120">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="bc854-121">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)  
 <span data-ttu-id="bc854-122">Sürüm, dizin ve yükleme durumu dahil olmak üzere belirli bir çalışma zamanı hakkında bilgi döndüren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-122">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="bc854-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)  
 <span data-ttu-id="bc854-124">Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-124">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="bc854-125">Tüm [ICLRStrongName](iclrstrongname-interface.md) YÖNTEMLERI standart com HResults döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc854-125">All the [ICLRStrongName](iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="bc854-126">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-126">ICLRStrongName2 Interface</span></span>](iclrstrongname2-interface.md)  
 <span data-ttu-id="bc854-127">, SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-127">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="bc854-128">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc854-128">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)  
 <span data-ttu-id="bc854-129">[ICLRTask arabiriminin](iclrtask-interface.md)tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc854-129">Provides all the functionality of the [ICLRTask Interface](iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bc854-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bc854-130">Related Sections</span></span>  

 [<span data-ttu-id="bc854-131">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="bc854-131">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="bc854-132">1,0 ve 1,1 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc854-132">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="bc854-133">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bc854-133">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="bc854-134">2,0, 3,0 ve 3,5 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc854-134">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="bc854-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="bc854-135">Hosting</span></span>](index.md)  
 <span data-ttu-id="bc854-136">.NET Framework barındırılmasını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="bc854-136">Introduces hosting in the .NET Framework.</span></span>

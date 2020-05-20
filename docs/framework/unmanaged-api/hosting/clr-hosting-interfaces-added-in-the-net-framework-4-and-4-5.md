---
title: .NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: a524c0b0e01fbde95ce2341874511960b3e5738e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616859"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="d47ca-102">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d47ca-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="d47ca-103">Bu bölümde, yönetilmeyen ana bilgisayarların .NET Framework 4, .NET Framework 4,5 ve sonraki sürümlerindeki ortak dil çalışma zamanını (CLR) bütünleştirmek için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d47ca-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="d47ca-104">Bu arabirimler, bir ana bilgisayarın çalışma zamanını yapılandırmak ve bir işleme yüklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="d47ca-105">.NET Framework 4 ' te başlayarak, tüm barındırma arabirimleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d47ca-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="d47ca-106">Yaşam süresi yönetimi ( `AddRef` ve `Release` ), kapsülleme (örtük bağlam) ve com ile kullanılır `QueryInterface` .</span><span class="sxs-lookup"><span data-stu-id="d47ca-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="d47ca-107">, Veya gibi COM türlerini kullanmaz `BSTR` `SAFEARRAY` `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="d47ca-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="d47ca-108">[Cocreateınstance işlevini](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)kullanan hiçbir Grup modeli, toplama veya kayıt defteri etkinleştirmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d47ca-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d47ca-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d47ca-109">In This Section</span></span>  
 [<span data-ttu-id="d47ca-110">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-110">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="d47ca-111">Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="d47ca-112">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-112">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)  
 <span data-ttu-id="d47ca-113">Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="d47ca-114">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-114">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)  
 <span data-ttu-id="d47ca-115">, Bir konağın çöp toplama segmentinin boyutunu ve çöp toplama sisteminin 1. kuşak en büyük boyut olan 0 ' dan büyük değerlere ayarlanmasını sağlayan [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini sağlar `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="d47ca-115">Provides the [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="d47ca-116">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-116">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)  
 <span data-ttu-id="d47ca-117">CLR 'nin belirli bir sürümünü döndüren, tüm yüklü CLRs 'leri listeleme, tüm işlem içi çalışma zamanlarını listeleme, etkinleştirme arabirimini geri döndürme ve bir derlemeyi derlemek için kullanılan CLR sürümünü bulma yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="d47ca-118">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-118">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="d47ca-119">İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan bir CLR arabirimi sağlayan [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) metodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-119">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="d47ca-120">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-120">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)  
 <span data-ttu-id="d47ca-121">Sürüm, dizin ve yükleme durumu dahil olmak üzere belirli bir çalışma zamanı hakkında bilgi döndüren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="d47ca-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)  
 <span data-ttu-id="d47ca-123">Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="d47ca-124">Tüm [ICLRStrongName](iclrstrongname-interface.md) YÖNTEMLERI standart com HResults döndürür.</span><span class="sxs-lookup"><span data-stu-id="d47ca-124">All the [ICLRStrongName](iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="d47ca-125">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-125">ICLRStrongName2 Interface</span></span>](iclrstrongname2-interface.md)  
 <span data-ttu-id="d47ca-126">, SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="d47ca-127">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47ca-127">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)  
 <span data-ttu-id="d47ca-128">[ICLRTask arabiriminin](iclrtask-interface.md)tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-128">Provides all the functionality of the [ICLRTask Interface](iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d47ca-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d47ca-129">Related Sections</span></span>  
 [<span data-ttu-id="d47ca-130">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="d47ca-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="d47ca-131">1,0 ve 1,1 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="d47ca-132">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d47ca-132">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="d47ca-133">2,0, 3,0 ve 3,5 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d47ca-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="d47ca-134">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d47ca-134">Hosting</span></span>](index.md)  
 <span data-ttu-id="d47ca-135">.NET Framework barındırılmasını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="d47ca-135">Introduces hosting in the .NET Framework.</span></span>

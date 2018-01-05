---
title: "Profil Oluşturma Numaralandırmaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84ac67b35bdbf686edb2fa35cc651aad4c19516b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-enumerations"></a><span data-ttu-id="72da7-102">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="72da7-102">Profiling Enumerations</span></span>
<span data-ttu-id="72da7-103">Bu bölümde, profil oluşturma API'si kullanan yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72da7-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72da7-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="72da7-104">In This Section</span></span>  
 [<span data-ttu-id="72da7-105">COR_PRF_CLAUSE_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="72da7-106">Kod yalnızca geçtiğini özel durum yan tümcesi veya sol türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="72da7-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="72da7-107">COR_PRF_CODEGEN_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="72da7-108">İle ayarlayabilirsiniz kod oluşturma bayrakları tanımlar [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72da7-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="72da7-109">COR_PRF_FINALIZER_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="72da7-110">Bir nesne için sonlandırıcıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="72da7-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="72da7-111">COR_PRF_GC_GENERATION Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="72da7-112">Çöp koleksiyonu oluşturma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72da7-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="72da7-113">COR_PRF_GC_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="72da7-114">Çöp toplama oluştuğunu nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72da7-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="72da7-115">COR_PRF_GC_ROOT_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="72da7-116">Çöp toplayıcı kök özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72da7-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="72da7-117">COR_PRF_GC_ROOT_KIND Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="72da7-118">Tarafından sunulan atık toplayıcı kök türünü gösteren [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="72da7-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="72da7-119">COR_PRF_HIGH_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="72da7-120">Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) profil oluşturucu belirtebilirsiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) onu yüklenirken yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72da7-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="72da7-121">COR_PRF_JIT_CACHE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="72da7-122">Önbelleğe alınan işlevi arama sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="72da7-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="72da7-123">COR_PRF_MISC Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="72da7-124">Özel tanımlayıcılarını belirtmek sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="72da7-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="72da7-125">COR_PRF_MODULE_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="72da7-126">Bir modül özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="72da7-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="72da7-127">COR_PRF_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="72da7-128">Davranış, özellikleri, olayları için profil oluşturucu abone istediği veya belirtmek için kullanılan değerler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="72da7-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="72da7-129">COR_PRF_RUNTIME_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="72da7-130">Ortak dil çalışma zamanı sürümü belirtmek değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="72da7-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="72da7-131">COR_PRF_SNAPSHOT_INFO Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="72da7-132">Profil Oluşturucu'nın her çağrıda anlık görüntü yığını ile ne kadar veri geçirmek için geri belirtir `StackSnapshotCallback` işlevi.</span><span class="sxs-lookup"><span data-stu-id="72da7-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="72da7-133">COR_PRF_STATIC_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="72da7-134">Bir statik alandır ve varsa, statik kalite, alan için geçerli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="72da7-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="72da7-135">COR_PRF_SUSPEND_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="72da7-136">Çalışma zamanı askıya alındı nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72da7-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="72da7-137">COR_PRF_TRANSITION_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72da7-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="72da7-138">Yönetilmeyen kod için veya tersi yönetilen bir geçiş nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72da7-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="72da7-139">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="72da7-139">Related Sections</span></span>  
 [<span data-ttu-id="72da7-140">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="72da7-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="72da7-141">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="72da7-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="72da7-142">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="72da7-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="72da7-143">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="72da7-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

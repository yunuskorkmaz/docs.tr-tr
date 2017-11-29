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
ms.openlocfilehash: 2e0b539c8e455040cc97f37f75476b0efe796abb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-enumerations"></a><span data-ttu-id="7859c-102">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7859c-102">Profiling Enumerations</span></span>
<span data-ttu-id="7859c-103">Bu bölümde, profil oluşturma API'si kullanan yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7859c-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7859c-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7859c-104">In This Section</span></span>  
 [<span data-ttu-id="7859c-105">COR_PRF_CLAUSE_TYPE numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="7859c-106">Kod yalnızca geçtiğini özel durum yan tümcesi veya sol türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7859c-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="7859c-107">Cor_prf_codegen_flags sabit listesi</span><span class="sxs-lookup"><span data-stu-id="7859c-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="7859c-108">İle ayarlayabilirsiniz kod oluşturma bayrakları tanımlar [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7859c-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="7859c-109">Cor_prf_fınalızer_flags numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="7859c-110">Bir nesne için sonlandırıcıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7859c-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="7859c-111">Cor_prf_gc_generatıon numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="7859c-112">Çöp koleksiyonu oluşturma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7859c-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="7859c-113">COR_PRF_GC_REASON numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="7859c-114">Çöp toplama oluştuğunu nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7859c-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="7859c-115">COR_PRF_GC_ROOT_FLAGS numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="7859c-116">Çöp toplayıcı kök özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7859c-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="7859c-117">Cor_prf_gc_root_kınd numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="7859c-118">Tarafından sunulan atık toplayıcı kök türünü gösteren [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="7859c-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="7859c-119">Cor_prf_hıgh_monıtor numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="7859c-120">Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) profil oluşturucu belirtebilirsiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) onu yüklenirken yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7859c-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="7859c-121">Cor_prf_jıt_cache numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="7859c-122">Önbelleğe alınan işlevi arama sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7859c-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="7859c-123">Cor_prf_mısc numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="7859c-124">Özel tanımlayıcılarını belirtmek sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7859c-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="7859c-125">COR_PRF_MODULE_FLAGS numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="7859c-126">Bir modül özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7859c-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="7859c-127">Cor_prf_monıtor numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="7859c-128">Davranış, özellikleri, olayları için profil oluşturucu abone istediği veya belirtmek için kullanılan değerler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="7859c-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="7859c-129">Cor_prf_runtıme_type numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="7859c-130">Ortak dil çalışma zamanı sürümü belirtmek değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7859c-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="7859c-131">Cor_prf_snapshot_ınfo numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="7859c-132">Profil Oluşturucu'nın her çağrıda anlık görüntü yığını ile ne kadar veri geçirmek için geri belirtir `StackSnapshotCallback` işlevi.</span><span class="sxs-lookup"><span data-stu-id="7859c-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="7859c-133">Cor_prf_statıc_type numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="7859c-134">Bir statik alandır ve varsa, statik kalite, alan için geçerli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7859c-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="7859c-135">COR_PRF_SUSPEND_REASON numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="7859c-136">Çalışma zamanı askıya alındı nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7859c-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="7859c-137">Cor_prf_transıtıon_reason numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7859c-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="7859c-138">Yönetilmeyen kod için veya tersi yönetilen bir geçiş nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7859c-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7859c-139">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7859c-139">Related Sections</span></span>  
 [<span data-ttu-id="7859c-140">Profil oluşturmaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="7859c-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="7859c-141">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7859c-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="7859c-142">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="7859c-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="7859c-143">Profil oluşturma yapıları</span><span class="sxs-lookup"><span data-stu-id="7859c-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

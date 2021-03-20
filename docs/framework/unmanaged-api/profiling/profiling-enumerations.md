---
description: 'Daha fazla bilgi için: profil oluşturma numaralandırmaları'
title: Profil Oluşturma Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: a4fcd812642698237d32afff5a681a99bf9cf12f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759071"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="4f247-103">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="4f247-103">Profiling Enumerations</span></span>

<span data-ttu-id="4f247-104">Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f247-104">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f247-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4f247-105">In This Section</span></span>  

 [<span data-ttu-id="4f247-106">COR_PRF_CLAUSE_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-106">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="4f247-107">Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-107">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="4f247-108">COR_PRF_CODEGEN_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4f247-108">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="4f247-109">[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f247-109">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="4f247-110">COR_PRF_FINALIZER_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-110">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="4f247-111">Bir nesne için sonlandırıcıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f247-111">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="4f247-112">COR_PRF_GC_GENERATION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-112">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="4f247-113">Çöp toplama oluşturmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f247-113">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="4f247-114">COR_PRF_GC_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-114">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="4f247-115">Çöp toplamanın oluşma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-115">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="4f247-116">COR_PRF_GC_ROOT_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-116">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="4f247-117">Çöp toplayıcı kökünün özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-117">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="4f247-118">COR_PRF_GC_ROOT_KIND Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-118">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="4f247-119">[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplayıcı kökünün türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-119">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="4f247-120">COR_PRF_HIGH_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-120">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="4f247-121">, Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metoduna belirtmesinin [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında bulunanlara ek olarak bayraklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f247-121">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="4f247-122">COR_PRF_JIT_CACHE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-122">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="4f247-123">Önbelleğe alınmış işlev aramasının sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-123">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="4f247-124">COR_PRF_MISC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-124">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="4f247-125">Özel tanımlayıcılar belirten sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4f247-125">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="4f247-126">COR_PRF_MODULE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-126">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="4f247-127">Modülün özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f247-127">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="4f247-128">COR_PRF_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-128">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="4f247-129">Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4f247-129">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="4f247-130">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-130">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="4f247-131">Ortak dil çalışma zamanının sürümünü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4f247-131">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="4f247-132">COR_PRF_SNAPSHOT_INFO Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-132">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="4f247-133">Profil oluşturucunun işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="4f247-133">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="4f247-134">COR_PRF_STATIC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-134">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="4f247-135">Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-135">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="4f247-136">COR_PRF_SUSPEND_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-136">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="4f247-137">Çalışma zamanının askıya alınma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-137">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="4f247-138">COR_PRF_TRANSITION_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f247-138">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="4f247-139">Yönetilmesinin yönetilmeyen koda veya tam tersi bir geçişin sebebini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-139">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  

 <span data-ttu-id="4f247-140">[COR_PRF_EVENTPIPE_PARAM_TYPE](cor-prf-eventpipe-param-type-enumeration.md) Bir EventPipe parametresinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f247-140">[COR_PRF_EVENTPIPE_PARAM_TYPE](cor-prf-eventpipe-param-type-enumeration.md) Indicates the type of an EventPipe parameter.</span></span>

 <span data-ttu-id="4f247-141">[COR_PRF_EVENTPIPE_LEVEL](cor-prf-eventpipe-level-enumeration.md) Bir EventPipe olayının düzeyini ındiklaştırır.</span><span class="sxs-lookup"><span data-stu-id="4f247-141">[COR_PRF_EVENTPIPE_LEVEL](cor-prf-eventpipe-level-enumeration.md) Indivates the level of an EventPipe event.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="4f247-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4f247-142">Related Sections</span></span>  

 [<span data-ttu-id="4f247-143">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4f247-143">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="4f247-144">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4f247-144">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="4f247-145">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4f247-145">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="4f247-146">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="4f247-146">Profiling Structures</span></span>](profiling-structures.md)

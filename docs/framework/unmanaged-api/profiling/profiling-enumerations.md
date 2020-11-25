---
title: Profil Oluşturma Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 8956a09cf76aa54452e8c020239e650e55d8a0d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701620"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="59732-102">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="59732-102">Profiling Enumerations</span></span>

<span data-ttu-id="59732-103">Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59732-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59732-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="59732-104">In This Section</span></span>  

 [<span data-ttu-id="59732-105">COR_PRF_CLAUSE_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="59732-106">Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="59732-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="59732-107">COR_PRF_CODEGEN_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="59732-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="59732-108">[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59732-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="59732-109">COR_PRF_FINALIZER_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="59732-110">Bir nesne için sonlandırıcıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="59732-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="59732-111">COR_PRF_GC_GENERATION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-111">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="59732-112">Çöp toplama oluşturmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59732-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="59732-113">COR_PRF_GC_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-113">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="59732-114">Çöp toplamanın oluşma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="59732-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="59732-115">COR_PRF_GC_ROOT_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="59732-116">Çöp toplayıcı kökünün özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="59732-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="59732-117">COR_PRF_GC_ROOT_KIND Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="59732-118">[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplayıcı kökünün türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="59732-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="59732-119">COR_PRF_HIGH_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="59732-120">, Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metoduna belirtmesinin [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında bulunanlara ek olarak bayraklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="59732-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="59732-121">COR_PRF_JIT_CACHE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-121">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="59732-122">Önbelleğe alınmış işlev aramasının sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="59732-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="59732-123">COR_PRF_MISC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-123">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="59732-124">Özel tanımlayıcılar belirten sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="59732-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="59732-125">COR_PRF_MODULE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="59732-126">Modülün özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59732-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="59732-127">COR_PRF_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-127">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="59732-128">Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="59732-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="59732-129">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="59732-130">Ortak dil çalışma zamanının sürümünü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="59732-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="59732-131">COR_PRF_SNAPSHOT_INFO Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="59732-132">Profil oluşturucunun işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="59732-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="59732-133">COR_PRF_STATIC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="59732-134">Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="59732-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="59732-135">COR_PRF_SUSPEND_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="59732-136">Çalışma zamanının askıya alınma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="59732-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="59732-137">COR_PRF_TRANSITION_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59732-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="59732-138">Yönetilmesinin yönetilmeyen koda veya tam tersi bir geçişin sebebini gösterir.</span><span class="sxs-lookup"><span data-stu-id="59732-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="59732-139">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="59732-139">Related Sections</span></span>  

 [<span data-ttu-id="59732-140">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="59732-140">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="59732-141">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="59732-141">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="59732-142">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="59732-142">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="59732-143">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="59732-143">Profiling Structures</span></span>](profiling-structures.md)

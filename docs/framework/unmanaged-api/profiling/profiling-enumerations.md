---
title: Profil Oluşturma Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 1a9781fa1b4b608152faa7d5edc80bd4866f0c81
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868141"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="08294-102">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="08294-102">Profiling Enumerations</span></span>
<span data-ttu-id="08294-103">Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08294-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08294-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="08294-104">In This Section</span></span>  
 [<span data-ttu-id="08294-105">COR_PRF_CLAUSE_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="08294-106">Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="08294-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="08294-107">COR_PRF_CODEGEN_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="08294-108">[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08294-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="08294-109">COR_PRF_FINALIZER_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="08294-110">Bir nesne için sonlandırıcıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="08294-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="08294-111">COR_PRF_GC_GENERATION Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-111">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="08294-112">Çöp toplama oluşturmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08294-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="08294-113">COR_PRF_GC_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-113">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="08294-114">Çöp toplamanın oluşma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="08294-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="08294-115">COR_PRF_GC_ROOT_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="08294-116">Çöp toplayıcı kökünün özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="08294-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="08294-117">COR_PRF_GC_ROOT_KIND Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="08294-118">[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplayıcı kökünün türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="08294-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="08294-119">COR_PRF_HIGH_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="08294-120">, Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metoduna belirtmesinin [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında bulunanlara ek olarak bayraklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="08294-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="08294-121">COR_PRF_JIT_CACHE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-121">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="08294-122">Önbelleğe alınmış işlev aramasının sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="08294-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="08294-123">COR_PRF_MISC Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-123">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="08294-124">Özel tanımlayıcılar belirten sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="08294-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="08294-125">COR_PRF_MODULE_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="08294-126">Modülün özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="08294-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="08294-127">COR_PRF_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-127">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="08294-128">Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="08294-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="08294-129">COR_PRF_RUNTIME_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="08294-130">Ortak dil çalışma zamanının sürümünü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="08294-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="08294-131">COR_PRF_SNAPSHOT_INFO Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="08294-132">Profiler 'ın `StackSnapshotCallback` işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="08294-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="08294-133">COR_PRF_STATIC_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="08294-134">Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="08294-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="08294-135">COR_PRF_SUSPEND_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="08294-136">Çalışma zamanının askıya alınma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="08294-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="08294-137">COR_PRF_TRANSITION_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="08294-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="08294-138">Yönetilmesinin yönetilmeyen koda veya tam tersi bir geçişin sebebini gösterir.</span><span class="sxs-lookup"><span data-stu-id="08294-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="08294-139">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="08294-139">Related Sections</span></span>  
 [<span data-ttu-id="08294-140">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="08294-140">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="08294-141">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08294-141">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="08294-142">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="08294-142">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="08294-143">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="08294-143">Profiling Structures</span></span>](profiling-structures.md)

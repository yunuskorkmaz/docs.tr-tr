---
title: Profil Oluşturma Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996352637f34b0b6c0d12e611a6d9e70ab85230e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757579"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="0eeed-102">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="0eeed-102">Profiling Enumerations</span></span>
<span data-ttu-id="0eeed-103">Bu bölümde, profil oluşturma API'SİNİN kullandığı yönetilmeyen numaralandırmaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="0eeed-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0eeed-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0eeed-104">In This Section</span></span>  
 [<span data-ttu-id="0eeed-105">COR_PRF_CLAUSE_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="0eeed-106">Kodu girdiğiniz özel durum yan tümcesi veya sol türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="0eeed-107">COR_PRF_CODEGEN_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="0eeed-108">Ayarlanabilir kod oluşturma bayraklarını tanımlayan [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0eeed-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="0eeed-109">COR_PRF_FINALIZER_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="0eeed-110">Bir nesnenin Sonlandırıcısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0eeed-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="0eeed-111">COR_PRF_GC_GENERATION Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="0eeed-112">Bir çöp toplama nesil tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0eeed-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="0eeed-113">COR_PRF_GC_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="0eeed-114">Çöp toplama oluştuğu nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="0eeed-115">COR_PRF_GC_ROOT_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="0eeed-116">Çöp toplayıcı kök özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="0eeed-117">COR_PRF_GC_ROOT_KIND Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="0eeed-118">Tarafından sunulan çöp toplayıcı kök türünü belirten [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="0eeed-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="0eeed-119">COR_PRF_HIGH_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="0eeed-120">Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Profiler'ı için belirtebileceğiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) , yüklenirken yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0eeed-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="0eeed-121">COR_PRF_JIT_CACHE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="0eeed-122">Önbelleğe alınan işlevi arama sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="0eeed-123">COR_PRF_MISC Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="0eeed-124">Özel tanımlayıcılardır belirten sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="0eeed-125">COR_PRF_MODULE_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="0eeed-126">Bir modül özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="0eeed-127">COR_PRF_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="0eeed-128">Davranış, özellikleri veya olayları profil oluşturucu abone olmak isteyen belirtmek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="0eeed-129">COR_PRF_RUNTIME_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="0eeed-130">Ortak dil çalışma zamanı sürümünü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="0eeed-131">COR_PRF_SNAPSHOT_INFO Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="0eeed-132">Ne kadar bir yığın profil oluşturucunun her çağrıda anlık görüntü ile geçirilecek veriler geri belirtir `StackSnapshotCallback` işlevi.</span><span class="sxs-lookup"><span data-stu-id="0eeed-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="0eeed-133">COR_PRF_STATIC_TYPE Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="0eeed-134">Bir statik alandır ve statik kalite bu durumda, alana uygulanan olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="0eeed-135">COR_PRF_SUSPEND_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="0eeed-136">Çalışma zamanı askıya alındı nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="0eeed-137">COR_PRF_TRANSITION_REASON Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0eeed-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="0eeed-138">Yönetilmeyen kod veya tam tersi yönetilen bir geçiş nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0eeed-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0eeed-139">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0eeed-139">Related Sections</span></span>  
 [<span data-ttu-id="0eeed-140">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0eeed-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="0eeed-141">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0eeed-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="0eeed-142">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0eeed-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="0eeed-143">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="0eeed-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

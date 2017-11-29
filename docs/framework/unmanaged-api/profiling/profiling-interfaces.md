---
title: "Profil Oluşturma Arabirimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c0423f9c8b01c1289e1107c0c16c59968a6e2a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-interfaces"></a><span data-ttu-id="8c167-102">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c167-102">Profiling Interfaces</span></span>
<span data-ttu-id="8c167-103">Bu bölümde ortak dil çalışma zamanı tarafından (CLR) çalıştırılan bir program profil sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c167-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c167-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8c167-104">In This Section</span></span>  
 [<span data-ttu-id="8c167-105">Iclrprofiling arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="8c167-106">Sağlar [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) çalışan bir işlemi eklemek bir profil oluşturucu etkinleştirir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c167-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="8c167-107">Icorprofilerassemblyreferenceprovider arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="8c167-108">Profil oluşturucu içinde ekleyeceksiniz derleme başvurularını CLR bildirmek profil oluşturucu etkinleştirir [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="8c167-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="8c167-109">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="8c167-110">CLR tarafından profil oluşturucu abone olaylar meydana geldiğinde kod profil oluşturucu bildirmek için kullanılan yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="8c167-111">Icorprofilercallback2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="8c167-112">Genişletir `ICorProfilerCallback` .NET Framework 2.0 ve sonraki sürümlerinde desteklenen geri aramalar arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8c167-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="8c167-113">Icorprofilercallback3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="8c167-114">CLR iletişim kurmak için kullandığı geri arama yöntemleri ekleme ve durum bilgilerini profil oluşturucu için ayırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="8c167-115">Icorprofilercallback4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="8c167-116">CLR Profil bilgilerini iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="8c167-117">Icorprofilercallback5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="8c167-118">Çöp toplama kökleri tarafından başvurulan nesne geçişli kapatma tanımlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="8c167-119">Icorprofilercallback6 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="8c167-120">Bir derlemesi yüklenirken bir profil oluşturucu bildirmek için CLR kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="8c167-121">ICorProfilerCallback7 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="8c167-122">Profil Oluşturucu bir bellek içi modülü ile ilişkili simgesi akış güncelleştirilir bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
 [<span data-ttu-id="8c167-123">Icorprofilerfunctioncontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-123">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="8c167-124">Kod profil oluşturucu nasıl JIT Derleyici kodu belirli bir yöntemi yeniden derlenmesi sırasında oluşturulmasına denetlemek için CLR ile iletişim kurmasına izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-124">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="8c167-125">Icorprofilerfunctionenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-125">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="8c167-126">CLR işlevlerde koleksiyonu sırayla yinelemek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-126">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="8c167-127">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="8c167-128">Kod profil oluşturucuları olayı izlemeyi denetlemek ve bilgi istemek için CLR ile iletişim kurmak için kullandığı için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-128">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="8c167-129">Icorprofilerınfo2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-129">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="8c167-130">Genişletir `ICorProfilerInfo` .NET Framework 2.0 ve sonraki sürümlerinde desteklenen yöntemleriyle arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8c167-130">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="8c167-131">Icorprofilerınfo3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-131">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="8c167-132">Genişletir `ICorProfilerInfo2` desteklenen yöntemleri arabirimiyle [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="8c167-132">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="8c167-133">Icorprofilerınfo4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-133">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="8c167-134">Kod profil oluşturucuları olayı izlemeyi denetlemek ve bilgi istemek için CLR ile iletişim kurmak için kullandıkları yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-134">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="8c167-135">Icorprofilerınfo5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-135">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="8c167-136">Kod profil oluşturucuları olayı izlemeyi denetlemek için CLR ile iletişim kurmak için kullandığı için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-136">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="8c167-137">ICorProfilerInfo6 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="8c167-138">Belirli bir NGen modüle ait olan ve belirli bir yöntemin gövdesine içermesinden tüm yöntemleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-138">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="8c167-139">ICorProfilerInfo7 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-139">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="8c167-140">Yeni uygulamak için bir yöntem meta verileri bir modüle tanımlanmış ve bir bellek içi simgesi akışına erişim sağlayan sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-140">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="8c167-141">Icorprofilermoduleenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-141">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="8c167-142">Uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu sırayla yinelemek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-142">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="8c167-143">Icorprofilerobjectenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-143">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="8c167-144">Bir koleksiyon tarafından üretilen dondurulmuş nesnelerin sırayla yinelemek için yöntemler sağlar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="8c167-144">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="8c167-145">Icorprofilerthreadenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-145">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="8c167-146">CLR iş parçacıkları koleksiyonu sırayla yinelemek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c167-146">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="8c167-147">Imethodmalloc arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c167-147">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="8c167-148">Sağlar [ayırma](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) yöntemi yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için bellek ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="8c167-148">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8c167-149">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8c167-149">Related Sections</span></span>  
 [<span data-ttu-id="8c167-150">Profil oluşturmaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="8c167-150">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="8c167-151">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="8c167-151">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="8c167-152">Profil oluşturma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="8c167-152">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="8c167-153">Profil oluşturma yapıları</span><span class="sxs-lookup"><span data-stu-id="8c167-153">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

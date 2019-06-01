---
title: Profil Oluşturma Arabirimleri
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97960a43e1d7ce625d96755a7c597a0425d0911
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457466"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="c3322-102">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c3322-102">Profiling Interfaces</span></span>
<span data-ttu-id="c3322-103">Bu bölümde, ortak dil çalışma zamanı tarafından (CLR) yürütülen bir programın profilini olanak tanıyan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3322-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3322-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c3322-104">In This Section</span></span>  
 [<span data-ttu-id="c3322-105">ICLRProfiling Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="c3322-106">Sağlar [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) yöntemi bir profil oluşturucunun bir çalışan işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="c3322-107">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="c3322-108">CLR, profil oluşturucu ekler derleme başvuruları bildirmek profil oluşturucu sağlar [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="c3322-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="c3322-109">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="c3322-110">Profil Oluşturucu abone olduğu olaylar meydana geldiğinde bir kod profil oluşturucu bildirmek için CLR tarafından kullanılan yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="c3322-111">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="c3322-112">Genişletir `ICorProfilerCallback` arabirimi ile .NET Framework 2.0 ve sonraki sürümlerinde desteklenen geri çağırmalar.</span><span class="sxs-lookup"><span data-stu-id="c3322-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="c3322-113">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="c3322-114">CLR iletişim kurmak için kullandığı geri çağırma yöntemleri ekleme ve ayırma profil oluşturucu için durum bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="c3322-115">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="c3322-116">CLR Profil Oluşturucu bilgiler iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="c3322-117">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="c3322-118">Çöp toplama kökleri tarafından başvurulan nesneleri geçişli kapatılmasını tanımlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="c3322-119">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="c3322-120">Bir derleme yüklenen bir profil oluşturucu bildirmek için CLR kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="c3322-121">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="c3322-122">Profil Oluşturucu bir bellek içi modül ile ilişkili simge akışı güncelleştirilmiş olduğunu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="c3322-123">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-123">ICorProfilerCallback8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
<span data-ttu-id="c3322-124">Dinamik bir yöntem JIT derlemesi başladı ve tamamlanmış olan profil oluşturucu bildirmek için ortak dil çalışma zamanı kullanan bir geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="c3322-125">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-125">ICorProfilerCallback9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
<span data-ttu-id="c3322-126">Toplanan ve daha sonra kaldırıldığında çöp dinamik bir yöntem olan profil oluşturucu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="c3322-127">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-127">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="c3322-128">Bir kod profil oluşturucu nasıl JIT Derleyici kodu belirli bir yöntem yeniden derlemeden oluşturmasını denetlemek için CLR ile iletişim kurmasına izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="c3322-129">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-129">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="c3322-130">Sıralı olarak CLR işlevler koleksiyonu üzerinden yineleme yapmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="c3322-131">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-131">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="c3322-132">Olay İzleme Denetim ve bilgi istemek için CLR ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="c3322-133">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-133">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="c3322-134">Genişletir `ICorProfilerInfo` arabirim yöntemleriyle .NET Framework 2.0 ve sonraki sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c3322-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="c3322-135">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3322-135">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="c3322-136">Genişletir `ICorProfilerInfo2` arabirim yöntemleriyle .NET Framework 4 ve sonraki sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c3322-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="c3322-137">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-137">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="c3322-138">Olay İzleme denetlemek ve bilgi istemek için CLR ile iletişim kurmak için kod profil oluşturucuları kullanmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="c3322-139">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-139">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="c3322-140">Olay İzleme denetlemek için CLR ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="c3322-141">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-141">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="c3322-142">Belirli bir NGen modüle ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış olan tüm yöntemleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="c3322-143">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-143">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="c3322-144">Yeni uygulamak için bir yöntem bir modül için meta verileri tanımlanmış ve bir bellek içi sembol akışına erişim sağlayan sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="c3322-145">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-145">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="c3322-146">Sıralı olarak uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu üzerinden yineleme yapmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="c3322-147">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-147">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="c3322-148">Tarafından oluşturulan donmuş nesneler koleksiyonunu sırayla yinelemek için yöntemler sağlar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="c3322-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="c3322-149">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-149">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="c3322-150">CLR iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3322-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="c3322-151">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3322-151">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="c3322-152">Sağlar [ayırma](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) yöntemi yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için bellek ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="c3322-152">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c3322-153">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c3322-153">Related Sections</span></span>  
 [<span data-ttu-id="c3322-154">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c3322-154">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="c3322-155">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c3322-155">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="c3322-156">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c3322-156">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="c3322-157">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="c3322-157">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

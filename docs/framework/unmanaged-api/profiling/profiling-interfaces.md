---
description: Daha fazla bilgi için bkz. profil oluşturma arabirimleri
title: Profil Oluşturma Arabirimleri
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: d35931c0caad93116d7ea26d29020d84e48ebc29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798933"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="46add-103">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="46add-103">Profiling Interfaces</span></span>

<span data-ttu-id="46add-104">Bu bölümde, ortak dil çalışma zamanı (CLR) tarafından yürütülen bir programın profilini oluşturma olanağı sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46add-104">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46add-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="46add-105">In This Section</span></span>  

 [<span data-ttu-id="46add-106">ICLRProfiling Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-106">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="46add-107">Bir profil oluşturucunun çalışan bir işleme iliştirmesine olanak sağlayan [AttachProfiler](iclrprofiling-attachprofiler-method.md) yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-107">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="46add-108">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-108">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="46add-109">Profiler 'ın [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması içinde ekleneceği derleme başvurularını clr 'ye bilgilendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-109">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="46add-110">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-110">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="46add-111">Profil oluşturucunun abone olduğu olaylar gerçekleştiğinde kod Profilcisi bildirmek için CLR tarafından kullanılan yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-111">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="46add-112">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-112">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="46add-113">Arabirimi, `ICorProfilerCallback` .NET Framework 2,0 ve sonraki sürümlerde desteklenen geri çağırmalar ile genişletir.</span><span class="sxs-lookup"><span data-stu-id="46add-113">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="46add-114">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-114">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="46add-115">CLR 'nin, bağlama ve ayırma durum bilgilerini profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-115">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="46add-116">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-116">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="46add-117">CLR 'nin bilgileri profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-117">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="46add-118">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-118">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="46add-119">Çöp toplama kökleri tarafından başvurulan nesnelerin geçişli kapanışını tanımlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-119">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="46add-120">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-120">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="46add-121">Bir derlemenin yüklendiği profil oluşturucuyu bilgilendirmek için CLR 'nin kullandığı bir geri çağırma yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-121">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="46add-122">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-122">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="46add-123">Ortak dil çalışma zamanının, bir bellek içi modülle ilişkili sembol akışının güncelleştirildiğini, profil oluşturucuyu bilgilendirmek için kullandığı bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-123">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="46add-124">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-124">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="46add-125">Ortak dil çalışma zamanının, dinamik bir yöntemin JıT derlemesinin başlatıldığını ve bittiğini bildiren profil oluşturucuyu bilgilendirmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-125">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="46add-126">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-126">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="46add-127">Ortak dil çalışma zamanının, dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılmadığını Profiler 'a bildirmek için kullandığı bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-127">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="46add-128">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-128">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="46add-129">Bir kod profil oluşturucunun, belirli bir yöntemi yeniden oluştururken JıT derleyicisinin nasıl kod üretdiğini denetlemek için CLR ile iletişim kurmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-129">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="46add-130">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-130">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="46add-131">CLR içindeki işlevlerin bir koleksiyonu aracılığıyla sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-131">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="46add-132">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-132">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="46add-133">Olay izleme ve istek bilgilerini denetlemek için CLR ile iletişim kurmak üzere kod profil oluşturucular tarafından kullanılacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-133">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="46add-134">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-134">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="46add-135">Arabirimi, `ICorProfilerInfo` .NET Framework 2,0 ve sonraki sürümlerde desteklenen yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="46add-135">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="46add-136">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-136">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="46add-137">Arabirimi, `ICorProfilerInfo2` .NET Framework 4 ve sonraki sürümlerinde desteklenen yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="46add-137">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="46add-138">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-138">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="46add-139">Olay izlemeyi denetlemek ve bilgi istemek üzere CLR ile iletişim kurmak için kod profil oluşturucular kullanan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-139">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="46add-140">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-140">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="46add-141">Olay izlemeyi denetlemek için CLR ile iletişim kurmak üzere kod profil oluşturucular tarafından kullanılacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-141">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="46add-142">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-142">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="46add-143">Belirli bir NGen modülüne ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış tüm yöntemlere bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-143">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="46add-144">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-144">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="46add-145">Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlar ve bellek içi sembol akışına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-145">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="46add-146">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-146">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="46add-147">Uygulama veya profil oluşturucu tarafından yüklenen bir modül koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-147">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="46add-148">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-148">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="46add-149">[Ngen.exe (yerel görüntü Oluşturucu)](../../tools/ngen-exe-native-image-generator.md)tarafından oluşturulan dondurulmuş nesnelerden oluşan bir koleksiyon aracılığıyla sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-149">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="46add-150">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-150">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="46add-151">CLR 'deki iş parçacığı koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-151">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="46add-152">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46add-152">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="46add-153">Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için bellek ayırmak üzere [ayırma](imethodmalloc-alloc-method.md) yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="46add-153">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="46add-154">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="46add-154">Related Sections</span></span>  

 [<span data-ttu-id="46add-155">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="46add-155">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="46add-156">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="46add-156">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="46add-157">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="46add-157">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="46add-158">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="46add-158">Profiling Structures</span></span>](profiling-structures.md)

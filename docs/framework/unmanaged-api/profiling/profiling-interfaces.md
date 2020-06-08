---
title: Profil Oluşturma Arabirimleri
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: f073794b4fdf89f289b70fed9967ee37b5f4e133
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494052"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="d6559-102">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d6559-102">Profiling Interfaces</span></span>
<span data-ttu-id="d6559-103">Bu bölümde, ortak dil çalışma zamanı (CLR) tarafından yürütülen bir programın profilini oluşturma olanağı sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6559-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6559-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d6559-104">In This Section</span></span>  
 [<span data-ttu-id="d6559-105">ICLRProfiling Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-105">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="d6559-106">Bir profil oluşturucunun çalışan bir işleme iliştirmesine olanak sağlayan [AttachProfiler](iclrprofiling-attachprofiler-method.md) yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-106">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="d6559-107">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="d6559-108">Profiler 'ın [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması içinde ekleneceği derleme başvurularını clr 'ye bilgilendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="d6559-109">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-109">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="d6559-110">Profil oluşturucunun abone olduğu olaylar gerçekleştiğinde kod Profilcisi bildirmek için CLR tarafından kullanılan yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="d6559-111">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-111">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="d6559-112">Arabirimi, `ICorProfilerCallback` .NET Framework 2,0 ve sonraki sürümlerde desteklenen geri çağırmalar ile genişletir.</span><span class="sxs-lookup"><span data-stu-id="d6559-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="d6559-113">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-113">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="d6559-114">CLR 'nin, bağlama ve ayırma durum bilgilerini profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="d6559-115">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-115">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="d6559-116">CLR 'nin bilgileri profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="d6559-117">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-117">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="d6559-118">Çöp toplama kökleri tarafından başvurulan nesnelerin geçişli kapanışını tanımlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="d6559-119">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-119">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="d6559-120">Bir derlemenin yüklendiği profil oluşturucuyu bilgilendirmek için CLR 'nin kullandığı bir geri çağırma yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="d6559-121">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-121">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="d6559-122">Ortak dil çalışma zamanının, bir bellek içi modülle ilişkili sembol akışının güncelleştirildiğini, profil oluşturucuyu bilgilendirmek için kullandığı bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="d6559-123">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="d6559-124">Ortak dil çalışma zamanının, dinamik bir yöntemin JıT derlemesinin başlatıldığını ve bittiğini bildiren profil oluşturucuyu bilgilendirmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="d6559-125">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-125">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="d6559-126">Ortak dil çalışma zamanının, dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılmadığını Profiler 'a bildirmek için kullandığı bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="d6559-127">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-127">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="d6559-128">Bir kod profil oluşturucunun, belirli bir yöntemi yeniden oluştururken JıT derleyicisinin nasıl kod üretdiğini denetlemek için CLR ile iletişim kurmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="d6559-129">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-129">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="d6559-130">CLR içindeki işlevlerin bir koleksiyonu aracılığıyla sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="d6559-131">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="d6559-132">Olay izleme ve istek bilgilerini denetlemek için CLR ile iletişim kurmak üzere kod profil oluşturucular tarafından kullanılacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="d6559-133">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-133">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="d6559-134">Arabirimi, `ICorProfilerInfo` .NET Framework 2,0 ve sonraki sürümlerde desteklenen yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="d6559-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="d6559-135">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-135">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="d6559-136">Arabirimi, `ICorProfilerInfo2` .NET Framework 4 ve sonraki sürümlerinde desteklenen yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="d6559-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="d6559-137">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-137">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="d6559-138">Olay izlemeyi denetlemek ve bilgi istemek üzere CLR ile iletişim kurmak için kod profil oluşturucular kullanan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="d6559-139">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="d6559-140">Olay izlemeyi denetlemek için CLR ile iletişim kurmak üzere kod profil oluşturucular tarafından kullanılacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="d6559-141">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-141">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="d6559-142">Belirli bir NGen modülüne ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış tüm yöntemlere bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="d6559-143">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-143">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="d6559-144">Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlar ve bellek içi sembol akışına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="d6559-145">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-145">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="d6559-146">Uygulama veya profil oluşturucu tarafından yüklenen bir modül koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="d6559-147">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-147">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="d6559-148">[Ngen. exe (yerel görüntü Oluşturucu)](../../tools/ngen-exe-native-image-generator.md)tarafından oluşturulan dondurulmuş nesneler koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="d6559-149">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-149">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="d6559-150">CLR 'deki iş parçacığı koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="d6559-151">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6559-151">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="d6559-152">Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için bellek ayırmak üzere [ayırma](imethodmalloc-alloc-method.md) yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6559-152">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d6559-153">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d6559-153">Related Sections</span></span>  
 [<span data-ttu-id="d6559-154">Profil oluşturmaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="d6559-154">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="d6559-155">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d6559-155">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="d6559-156">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d6559-156">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="d6559-157">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="d6559-157">Profiling Structures</span></span>](profiling-structures.md)

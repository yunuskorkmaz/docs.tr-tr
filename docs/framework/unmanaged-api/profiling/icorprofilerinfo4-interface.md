---
title: ICorProfilerInfo4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
ms.openlocfilehash: cbd7c0d8fff55766a98e727ce22c77dd5214611b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448009"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="9e6bc-102">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="9e6bc-103">Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="9e6bc-104">.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-104">.</span></span> <span data-ttu-id="9e6bc-105">`ICorProfilerInfo4` arabirimi, diğer `ICorProfilerInfo` arabirimlerinin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="9e6bc-106">.NET Framework 4,5 ' ye eklenen tam zamanında (JıT) yeniden derlemeyi desteklemek için yeni yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e6bc-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e6bc-107">Methods</span></span>  
  
|<span data-ttu-id="9e6bc-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9e6bc-108">Method</span></span>|<span data-ttu-id="9e6bc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e6bc-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e6bc-110">EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="9e6bc-111">Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="9e6bc-112">EnumThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="9e6bc-113">Profili oluşturulan işlemdeki tüm yönetilen iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="9e6bc-114">GetCodeInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="9e6bc-115">Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="9e6bc-116">GetFunctionFromIP2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="9e6bc-117">Yönetilen bir kod yönerge işaretçisini belirtilen işlevin JıT yeniden derlenmiş sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="9e6bc-118">GetILToNativeMapping2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="9e6bc-119">Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="9e6bc-120">GetObjectSize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="9e6bc-121">Belirtilen nesnenin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="9e6bc-122">GetReJITIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="9e6bc-123">Hala ayrılan belirtilen işlevin tüm JıT yeniden derlenmiş sürümlerini tanımlayan bir kimlik dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="9e6bc-124">InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="9e6bc-125">Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="9e6bc-126">RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="9e6bc-127">Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="9e6bc-128">RequestRevert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="9e6bc-129">Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e6bc-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e6bc-130">Remarks</span></span>  
 <span data-ttu-id="9e6bc-131">CLR, serbest iş parçacıklı modeli kullanarak `ICorProfilerInfo4` arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="9e6bc-132">Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="9e6bc-133">Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e6bc-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e6bc-134">Requirements</span></span>  
 <span data-ttu-id="9e6bc-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e6bc-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e6bc-136">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9e6bc-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e6bc-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9e6bc-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e6bc-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e6bc-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e6bc-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e6bc-139">See also</span></span>

- [<span data-ttu-id="9e6bc-140">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e6bc-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9e6bc-141">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e6bc-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

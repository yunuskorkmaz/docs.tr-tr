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
ms.openlocfilehash: c3e623b0b5f8b49e043fe3a1aa8311558e573573
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682841"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="1db2b-102">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1db2b-102">ICorProfilerInfo4 Interface</span></span>

<span data-ttu-id="1db2b-103">Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1db2b-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="1db2b-104">.</span><span class="sxs-lookup"><span data-stu-id="1db2b-104">.</span></span> <span data-ttu-id="1db2b-105">`ICorProfilerInfo4`Arabirim, diğer arabirimlerin bir uzantısıdır `ICorProfilerInfo` .</span><span class="sxs-lookup"><span data-stu-id="1db2b-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="1db2b-106">.NET Framework 4,5 ' ye eklenen tam zamanında (JıT) yeniden derlemeyi desteklemek için yeni yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1db2b-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1db2b-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1db2b-107">Methods</span></span>  
  
|<span data-ttu-id="1db2b-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1db2b-108">Method</span></span>|<span data-ttu-id="1db2b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1db2b-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1db2b-110">EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-110">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="1db2b-111">Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="1db2b-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="1db2b-112">EnumThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-112">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="1db2b-113">Profili oluşturulan işlemdeki tüm yönetilen iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="1db2b-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="1db2b-114">GetCodeInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-114">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="1db2b-115">Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.</span><span class="sxs-lookup"><span data-stu-id="1db2b-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="1db2b-116">GetFunctionFromIP2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-116">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="1db2b-117">Yönetilen bir kod yönerge işaretçisini belirtilen işlevin JıT yeniden derlenmiş sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="1db2b-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="1db2b-118">GetILToNativeMapping2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-118">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="1db2b-119">Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="1db2b-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="1db2b-120">GetObjectSize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-120">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="1db2b-121">Belirtilen nesnenin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1db2b-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="1db2b-122">GetReJITIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-122">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="1db2b-123">Hala ayrılan belirtilen işlevin tüm JıT yeniden derlenmiş sürümlerini tanımlayan bir kimlik dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1db2b-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="1db2b-124">InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-124">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="1db2b-125">Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="1db2b-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="1db2b-126">RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-126">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="1db2b-127">Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="1db2b-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="1db2b-128">RequestRevert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db2b-128">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="1db2b-129">Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1db2b-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db2b-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1db2b-130">Remarks</span></span>  

 <span data-ttu-id="1db2b-131">CLR, `ICorProfilerInfo4` serbest iş parçacıklı modeli kullanarak arabirimin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="1db2b-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="1db2b-132">Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="1db2b-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="1db2b-133">Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="1db2b-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1db2b-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1db2b-134">Requirements</span></span>  

 <span data-ttu-id="1db2b-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1db2b-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db2b-136">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1db2b-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1db2b-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1db2b-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1db2b-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1db2b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db2b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1db2b-139">See also</span></span>

- [<span data-ttu-id="1db2b-140">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1db2b-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1db2b-141">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1db2b-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

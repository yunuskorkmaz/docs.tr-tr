---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4 Interface'
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
ms.openlocfilehash: 94e33be74ccffea3fa9a0e51e317a6888596606d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794513"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="8d32e-103">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d32e-103">ICorProfilerInfo4 Interface</span></span>

<span data-ttu-id="8d32e-104">Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d32e-104">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="8d32e-105">.</span><span class="sxs-lookup"><span data-stu-id="8d32e-105">.</span></span> <span data-ttu-id="8d32e-106">`ICorProfilerInfo4`Arabirim, diğer arabirimlerin bir uzantısıdır `ICorProfilerInfo` .</span><span class="sxs-lookup"><span data-stu-id="8d32e-106">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="8d32e-107">.NET Framework 4,5 ' ye eklenen tam zamanında (JıT) yeniden derlemeyi desteklemek için yeni yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d32e-107">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d32e-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8d32e-108">Methods</span></span>  
  
|<span data-ttu-id="8d32e-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8d32e-109">Method</span></span>|<span data-ttu-id="8d32e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d32e-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d32e-111">EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-111">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="8d32e-112">Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32e-112">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="8d32e-113">EnumThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-113">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="8d32e-114">Profili oluşturulan işlemdeki tüm yönetilen iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="8d32e-114">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="8d32e-115">GetCodeInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-115">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="8d32e-116">Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.</span><span class="sxs-lookup"><span data-stu-id="8d32e-116">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="8d32e-117">GetFunctionFromIP2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-117">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="8d32e-118">Yönetilen bir kod yönerge işaretçisini belirtilen işlevin JıT yeniden derlenmiş sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="8d32e-118">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="8d32e-119">GetILToNativeMapping2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-119">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="8d32e-120">Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="8d32e-120">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="8d32e-121">GetObjectSize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-121">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="8d32e-122">Belirtilen nesnenin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32e-122">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="8d32e-123">GetReJITIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-123">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="8d32e-124">Hala ayrılan belirtilen işlevin tüm JıT yeniden derlenmiş sürümlerini tanımlayan bir kimlik dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32e-124">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="8d32e-125">InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-125">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="8d32e-126">Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d32e-126">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="8d32e-127">RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-127">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="8d32e-128">Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="8d32e-128">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="8d32e-129">RequestRevert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d32e-129">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="8d32e-130">Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32e-130">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d32e-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d32e-131">Remarks</span></span>  

 <span data-ttu-id="8d32e-132">CLR, `ICorProfilerInfo4` serbest iş parçacıklı modeli kullanarak arabirimin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="8d32e-132">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="8d32e-133">Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32e-133">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="8d32e-134">Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="8d32e-134">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d32e-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d32e-135">Requirements</span></span>  

 <span data-ttu-id="8d32e-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d32e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d32e-137">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8d32e-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d32e-138">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8d32e-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d32e-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d32e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d32e-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d32e-140">See also</span></span>

- [<span data-ttu-id="8d32e-141">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8d32e-141">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8d32e-142">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d32e-142">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

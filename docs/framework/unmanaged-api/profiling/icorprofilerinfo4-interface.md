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
ms.openlocfilehash: c287b630aee58c6795ef405cc1801149e220fd51
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868427"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="dc5b7-102">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="dc5b7-103">Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="dc5b7-104">.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-104">.</span></span> <span data-ttu-id="dc5b7-105">`ICorProfilerInfo4` arabirimi, diğer `ICorProfilerInfo` arabirimlerinin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="dc5b7-106">.NET Framework 4,5 ' ye eklenen tam zamanında (JıT) yeniden derlemeyi desteklemek için yeni yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc5b7-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dc5b7-107">Methods</span></span>  
  
|<span data-ttu-id="dc5b7-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dc5b7-108">Method</span></span>|<span data-ttu-id="dc5b7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc5b7-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc5b7-110">EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-110">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="dc5b7-111">Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="dc5b7-112">EnumThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-112">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="dc5b7-113">Profili oluşturulan işlemdeki tüm yönetilen iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="dc5b7-114">GetCodeInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-114">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="dc5b7-115">Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="dc5b7-116">GetFunctionFromIP2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-116">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="dc5b7-117">Yönetilen bir kod yönerge işaretçisini belirtilen işlevin JıT yeniden derlenmiş sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="dc5b7-118">GetILToNativeMapping2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-118">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="dc5b7-119">Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="dc5b7-120">GetObjectSize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-120">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="dc5b7-121">Belirtilen nesnenin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="dc5b7-122">GetReJITIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-122">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="dc5b7-123">Hala ayrılan belirtilen işlevin tüm JıT yeniden derlenmiş sürümlerini tanımlayan bir kimlik dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="dc5b7-124">InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-124">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="dc5b7-125">Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="dc5b7-126">RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-126">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="dc5b7-127">Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="dc5b7-128">RequestRevert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-128">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="dc5b7-129">Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc5b7-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc5b7-130">Remarks</span></span>  
 <span data-ttu-id="dc5b7-131">CLR, serbest iş parçacıklı modeli kullanarak `ICorProfilerInfo4` arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="dc5b7-132">Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="dc5b7-133">Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc5b7-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc5b7-134">Requirements</span></span>  
 <span data-ttu-id="dc5b7-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc5b7-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc5b7-136">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dc5b7-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc5b7-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dc5b7-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc5b7-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc5b7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc5b7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc5b7-139">See also</span></span>

- [<span data-ttu-id="dc5b7-140">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc5b7-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="dc5b7-141">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc5b7-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

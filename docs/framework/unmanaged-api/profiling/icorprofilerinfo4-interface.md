---
title: ICorProfilerInfo4 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db91347ad2c951c28ea7b653336450929d37bdcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="afb39-102">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afb39-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="afb39-103">Kod profil oluşturucuları ortak dil çalışma zamanı (CLR) olayı izlemeyi denetlemek için ve istek bilgileri ile iletişim kurmak için kullandığı yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="afb39-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="afb39-104">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="afb39-104">.</span></span> <span data-ttu-id="afb39-105">`ICorProfilerInfo4` Arabirimi uzantısıdır diğer `ICorProfilerInfo` arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="afb39-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="afb39-106">Tam zamanında (JIT) yeniden derlenmek, eklenen desteklemek için yeni yöntemler sağlar [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="afb39-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afb39-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="afb39-107">Methods</span></span>  
  
|<span data-ttu-id="afb39-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="afb39-108">Method</span></span>|<span data-ttu-id="afb39-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afb39-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="afb39-110">Enumjıtedfunctions2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="afb39-111">JIT derlenmiş ve JIT yeniden derlenmesi daha önce tüm işlevleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="afb39-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="afb39-112">EnumThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="afb39-113">Bir numaralandırıcı sırayla tüm yönetilen iş parçacıklarında profili işlem koleksiyonunu yinelemek için yöntemler sağlayan alır.</span><span class="sxs-lookup"><span data-stu-id="afb39-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="afb39-114">Getcodeınfo3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="afb39-115">Belirtilen işlev JIT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsam alır.</span><span class="sxs-lookup"><span data-stu-id="afb39-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="afb39-116">Getfunctionfromıp2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="afb39-117">Yönetilen kod yönerge işaretçisi belirtilen işlev JIT yeniden derlenmesi sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="afb39-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="afb39-118">Getıltonativemapping2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="afb39-119">Belirtilen işlev JIT yeniden derlenmesi sürümünde yer alan kodu için yerel uzaklık için Ara dili (MSIL) kaydırır Microsoft'tan bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="afb39-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="afb39-120">GetObjectSize2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="afb39-121">Belirtilen nesnenin boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="afb39-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="afb39-122">Getrejıtıds yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="afb39-123">Hala ayrılan tüm JIT yeniden derlenmesi sürümlerini belirtilen işlev tanımlamak kimlikleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="afb39-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="afb39-124">Initializecurrentthread yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="afb39-125">Bu kilitlenme önlenebilir şekilde aynı iş parçacığı üzerinde API çağrılarının sonraki profil oluşturucu çalıştırılmasının geçerli iş parçacığının başlatır.</span><span class="sxs-lookup"><span data-stu-id="afb39-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="afb39-126">Requestrejıt yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="afb39-127">JIT derleme belirtilen işlevler tüm örneklerinin ister.</span><span class="sxs-lookup"><span data-stu-id="afb39-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="afb39-128">RequestRevert yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb39-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="afb39-129">Özgün sürümlerine belirtilen işleve tüm örneklerini döner.</span><span class="sxs-lookup"><span data-stu-id="afb39-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afb39-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afb39-130">Remarks</span></span>  
 <span data-ttu-id="afb39-131">CLR yöntemlerini uygular `ICorProfilerInfo4` ücretsiz iş parçacıklı modeli kullanarak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="afb39-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="afb39-132">Her yöntem, başarı veya hata durumunu göstermek için bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="afb39-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="afb39-133">Olası dönüş kodları listesi için CorError.h dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="afb39-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb39-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afb39-134">Requirements</span></span>  
 <span data-ttu-id="afb39-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb39-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb39-136">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="afb39-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="afb39-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afb39-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afb39-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb39-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb39-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afb39-139">See Also</span></span>  
 [<span data-ttu-id="afb39-140">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="afb39-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="afb39-141">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="afb39-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

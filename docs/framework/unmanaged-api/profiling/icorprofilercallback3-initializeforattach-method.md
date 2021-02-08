---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback3:: InitializeForAttach yöntemi'
title: ICorProfilerCallback3::InitializeForAttach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: b3c5b8701df9e680e4fcbd57f4e08395dfe0b8da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788819"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="0e096-103">ICorProfilerCallback3::InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e096-103">ICorProfilerCallback3::InitializeForAttach Method</span></span>

<span data-ttu-id="0e096-104">Profil oluşturucuya bir iliştirme işleminden sonra durumunu başlatma fırsatı vermek için ortak dil çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="0e096-104">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e096-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e096-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e096-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e096-106">Parameters</span></span>  

 `pCorProfilerInfoUnk`  
 <span data-ttu-id="0e096-107">'ndaki Arabirim için arabirim işaretçisi `ICorProfilerInfo*` .</span><span class="sxs-lookup"><span data-stu-id="0e096-107">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="0e096-108">'ndaki Parametresindeki [ıclrprofile:: AttachProfiler](iclrprofiling-attachprofiler-method.md) metoduna geçirilen verilere yönelik bir işaretçi `pvClientData` .</span><span class="sxs-lookup"><span data-stu-id="0e096-108">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="0e096-109">Bu parametre null ise `cbClientData` 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="0e096-109">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="0e096-110">CLR bu belleği öğesinden döndüğünde serbest bırakır `InitializeForAttach` .</span><span class="sxs-lookup"><span data-stu-id="0e096-110">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="0e096-111">'ndaki Öğesinin işaret ettiği verilerin bayt cinsinden boyutu `pvClientData` .</span><span class="sxs-lookup"><span data-stu-id="0e096-111">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e096-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e096-112">Remarks</span></span>  

 <span data-ttu-id="0e096-113">CLR, `InitializeForAttach` profil oluşturucuya geri çağırmaları isteme fırsatı vermek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="0e096-113">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e096-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e096-114">Requirements</span></span>  

 <span data-ttu-id="0e096-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e096-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e096-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0e096-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0e096-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0e096-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e096-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e096-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e096-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e096-119">See also</span></span>

- [<span data-ttu-id="0e096-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e096-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0e096-121">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e096-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="0e096-122">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0e096-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0e096-123">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e096-123">Profiling</span></span>](index.md)

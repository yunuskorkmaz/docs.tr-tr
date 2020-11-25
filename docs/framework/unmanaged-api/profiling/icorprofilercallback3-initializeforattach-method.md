---
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
ms.openlocfilehash: c85bba9a5d913820b69cbc214275b733a53197ee
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729453"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="e7481-102">ICorProfilerCallback3::InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7481-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>

<span data-ttu-id="e7481-103">Profil oluşturucuya bir iliştirme işleminden sonra durumunu başlatma fırsatı vermek için ortak dil çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e7481-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7481-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e7481-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7481-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7481-105">Parameters</span></span>  

 `pCorProfilerInfoUnk`  
 <span data-ttu-id="e7481-106">'ndaki Arabirim için arabirim işaretçisi `ICorProfilerInfo*` .</span><span class="sxs-lookup"><span data-stu-id="e7481-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="e7481-107">'ndaki Parametresindeki [ıclrprofile:: AttachProfiler](iclrprofiling-attachprofiler-method.md) metoduna geçirilen verilere yönelik bir işaretçi `pvClientData` .</span><span class="sxs-lookup"><span data-stu-id="e7481-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="e7481-108">Bu parametre null ise `cbClientData` 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="e7481-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="e7481-109">CLR bu belleği öğesinden döndüğünde serbest bırakır `InitializeForAttach` .</span><span class="sxs-lookup"><span data-stu-id="e7481-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="e7481-110">'ndaki Öğesinin işaret ettiği verilerin bayt cinsinden boyutu `pvClientData` .</span><span class="sxs-lookup"><span data-stu-id="e7481-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7481-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7481-111">Remarks</span></span>  

 <span data-ttu-id="e7481-112">CLR, `InitializeForAttach` profil oluşturucuya geri çağırmaları isteme fırsatı vermek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="e7481-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7481-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7481-113">Requirements</span></span>  

 <span data-ttu-id="e7481-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7481-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7481-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e7481-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7481-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e7481-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7481-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7481-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7481-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7481-118">See also</span></span>

- [<span data-ttu-id="e7481-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7481-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e7481-120">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7481-120">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e7481-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e7481-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e7481-122">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7481-122">Profiling</span></span>](index.md)

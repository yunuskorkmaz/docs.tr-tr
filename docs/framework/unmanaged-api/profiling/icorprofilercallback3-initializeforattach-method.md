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
ms.openlocfilehash: 047516574595f9ffcd61360f51823da73a2f9733
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439524"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="9adf5-102">ICorProfilerCallback3::InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9adf5-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="9adf5-103">Profil oluşturucuya bir iliştirme işleminden sonra durumunu başlatma fırsatı vermek için ortak dil çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9adf5-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9adf5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9adf5-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9adf5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9adf5-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="9adf5-106">'ndaki `ICorProfilerInfo*` arabirimi için bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9adf5-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="9adf5-107">'ndaki `pvClientData` parametresindeki [ıclrprofile:: AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) yöntemine geçirilen verilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9adf5-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="9adf5-108">Bu parametre null ise, `cbClientData` 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="9adf5-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="9adf5-109">CLR `InitializeForAttach`'den döndüğünde bu belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="9adf5-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="9adf5-110">'ndaki `pvClientData` tarafından işaret edilen verilerin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="9adf5-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9adf5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9adf5-111">Remarks</span></span>  
 <span data-ttu-id="9adf5-112">CLR, profil oluşturucuya geri çağırma istekleri için bir fırsat vermek üzere `InitializeForAttach` çağırır.</span><span class="sxs-lookup"><span data-stu-id="9adf5-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9adf5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9adf5-113">Requirements</span></span>  
 <span data-ttu-id="9adf5-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9adf5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9adf5-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9adf5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9adf5-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9adf5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9adf5-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9adf5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9adf5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9adf5-118">See also</span></span>

- [<span data-ttu-id="9adf5-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9adf5-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9adf5-120">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9adf5-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9adf5-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9adf5-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9adf5-122">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9adf5-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

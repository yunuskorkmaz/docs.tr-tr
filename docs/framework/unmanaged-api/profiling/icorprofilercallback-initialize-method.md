---
title: ICorProfilerCallback::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: e4a003b30c495852a3a68d44d92bef35c3ed7812
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866305"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="4b07a-102">ICorProfilerCallback::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b07a-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="4b07a-103">Her yeni ortak dil çalışma zamanı (CLR) uygulaması başlatıldığında kod profil oluşturucuyu başlatmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="4b07a-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b07a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b07a-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b07a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b07a-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="4b07a-106">\[in] bir [ICorProfilerInfo](icorprofilerinfo-interface.md) arabirimi işaretçisi için sorgu gereken bir [IUnknown](/cpp/atl/iunknown) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4b07a-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="4b07a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b07a-107">Remarks</span></span>  
 <span data-ttu-id="4b07a-108">`Initialize` çağrısı, sabit olan geri çağırmaları etkinleştirmek (veya devre dışı bırakmak) için tek fırsattır.</span><span class="sxs-lookup"><span data-stu-id="4b07a-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="4b07a-109">`Initialize` çağrısı tarafından bir geri çağırma etkinleştirildikten sonra, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)kullanılarak daha sonra devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="4b07a-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="4b07a-110">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) sabit listesinin COR_PRF_MONITOR_IMMUTABLE değeri, hangi olayların sabit olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b07a-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b07a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b07a-111">Requirements</span></span>  
 <span data-ttu-id="4b07a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b07a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b07a-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4b07a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b07a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4b07a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b07a-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b07a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b07a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b07a-116">See also</span></span>

- [<span data-ttu-id="4b07a-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b07a-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4b07a-118">Shutdown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b07a-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)

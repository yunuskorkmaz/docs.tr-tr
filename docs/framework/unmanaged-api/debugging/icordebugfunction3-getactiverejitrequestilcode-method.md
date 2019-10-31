---
title: ICorDebugFunction3::GetActiveReJitRequestILCode Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 0e706861237ed08700ef0abcc424b6f1de5f462c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134649"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="8b2bb-102">ICorDebugFunction3::GetActiveReJitRequestILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="8b2bb-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="8b2bb-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="8b2bb-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8b2bb-104">Etkin bir ReJIT isteğinden Il 'yi içeren bir [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2bb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b2bb-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b2bb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b2bb-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="8b2bb-107">Etkin bir ReJIT isteğinden Il 'ye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b2bb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b2bb-108">Remarks</span></span>  
 <span data-ttu-id="8b2bb-109">Bu `ICorDebugFunction3` nesnesi tarafından temsil edilen yöntemin etkin bir ReJIT isteği varsa, `ppReJitedILCode` Il 'ye bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="8b2bb-110">Ortak bir durum olan etkin istek yoksa `ppReJitedILCode` **null**olur.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="8b2bb-111">Yeniden JIT isteği, yürütme, [ICorProfilerCallback4:: Getrejparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) yöntem çağrısından çağrıldıktan hemen sonra etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="8b2bb-112">Henüz JıT derlenemez ve iş parçacıkları kodun orijinal sürümünde hala yürütülüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="8b2bb-113">Profil Oluşturucu [ICorProfilerInfo4:: Requestdöndürülüyor](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) yöntemine yapılan çağrı sırasında yeniden JIT isteği devre dışı olur.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="8b2bb-114">Il geri alındıktan sonra bile, bir iş parçacığı yine de JıT-yeniden derleme (ReJIT) kodunda yürütülüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b2bb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b2bb-115">Requirements</span></span>  
 <span data-ttu-id="8b2bb-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b2bb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b2bb-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8b2bb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b2bb-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8b2bb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b2bb-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b2bb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b2bb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b2bb-120">See also</span></span>

- [<span data-ttu-id="8b2bb-121">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b2bb-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="8b2bb-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b2bb-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8b2bb-123">ReJIT: nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8b2bb-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)

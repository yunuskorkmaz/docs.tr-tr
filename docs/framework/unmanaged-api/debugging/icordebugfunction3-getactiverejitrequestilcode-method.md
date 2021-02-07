---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugFunction3:: Getactiverejrequestilcode yöntemi'
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
ms.openlocfilehash: 9225c5cdf97395b7e1b11c61d653cab8d52031c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692127"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="d62be-103">ICorDebugFunction3::GetActiveReJitRequestILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="d62be-103">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>

<span data-ttu-id="d62be-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="d62be-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d62be-105">Etkin bir ReJIT isteğinden Il 'yi içeren bir [ICorDebugILCode](icordebugilcode-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d62be-105">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d62be-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d62be-106">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d62be-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d62be-107">Parameters</span></span>  

 `ppReJitedILCode`  
 <span data-ttu-id="d62be-108">Etkin bir ReJIT isteğinden Il 'ye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d62be-108">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d62be-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d62be-109">Remarks</span></span>  

 <span data-ttu-id="d62be-110">Bu nesne tarafından temsil edilen yöntemin `ICorDebugFunction3` etkin bir ReJIT isteği varsa, `ppReJitedILCode` Il 'ye bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d62be-110">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="d62be-111">Ortak bir durum olan etkin istek yoksa, `ppReJitedILCode` **null** olur.</span><span class="sxs-lookup"><span data-stu-id="d62be-111">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="d62be-112">Yeniden JIT isteği, yürütme, [ICorProfilerCallback4:: Getrejparameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) yöntem çağrısından çağrıldıktan hemen sonra etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="d62be-112">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="d62be-113">Henüz JıT derlenemez ve iş parçacıkları kodun orijinal sürümünde hala yürütülüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d62be-113">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="d62be-114">Profil Oluşturucu [ICorProfilerInfo4:: Requestdöndürülüyor](../profiling/icorprofilerinfo4-requestrevert-method.md) yöntemine yapılan çağrı sırasında yeniden JIT isteği devre dışı olur.</span><span class="sxs-lookup"><span data-stu-id="d62be-114">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="d62be-115">Il geri alındıktan sonra bile, bir iş parçacığı yine de JıT-yeniden derleme (ReJIT) kodunda yürütülüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d62be-115">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d62be-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d62be-116">Requirements</span></span>  

 <span data-ttu-id="d62be-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d62be-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d62be-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d62be-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d62be-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d62be-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d62be-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d62be-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62be-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d62be-121">See also</span></span>

- [<span data-ttu-id="d62be-122">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d62be-122">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="d62be-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d62be-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d62be-124">ReJIT: A How-To Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d62be-124">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)

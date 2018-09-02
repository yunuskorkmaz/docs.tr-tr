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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c49a9543c7bfeb9882144fba74b9c48cfba64890
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393395"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="dcbe6-102">ICorDebugFunction3::GetActiveReJitRequestILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="dcbe6-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="dcbe6-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="dcbe6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="dcbe6-104">Bir arabirim işaretçisi alır bir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) , etkin bir ReJIT istek IL içerir.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbe6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcbe6-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcbe6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcbe6-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="dcbe6-107">Etkin bir ReJIT istek IL işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcbe6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcbe6-108">Remarks</span></span>  
 <span data-ttu-id="dcbe6-109">Yöntemi bu tarafından temsil edilen varsa `ICorDebugFunction3` nesne sahip etkin bir ReJIT istek `ppReJitedILCode` , IL için bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="dcbe6-110">Yaygın bir durumda ise hiçbir etkin istek olup olmadığını `ppReJitedILCode` olduğu **null**.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="dcbe6-111">Yürütmeyi hemen döndürür sonra ReJIT isteği etkin hale gelir [Icorprofilercallback4::getrejıtparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="dcbe6-112">Bunu henüz JIT olarak derlenmiş olmayabilir ve iş parçacığı hala kod'in özgün sürümünde yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="dcbe6-113">Profil oluşturucu çağrısı sırasında ReJIT istek devre dışı kalmadan [Icorprofilerınfo4::requestrevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="dcbe6-114">IL bile dönüştürüldükten sonra bir iş parçacığı JIT yeniden derlenen (ReJIT) kodda hala yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcbe6-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcbe6-115">Requirements</span></span>  
 <span data-ttu-id="dcbe6-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcbe6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcbe6-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcbe6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcbe6-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcbe6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcbe6-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcbe6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbe6-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dcbe6-120">See Also</span></span>  
 [<span data-ttu-id="dcbe6-121">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcbe6-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 [<span data-ttu-id="dcbe6-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dcbe6-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dcbe6-123">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dcbe6-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)

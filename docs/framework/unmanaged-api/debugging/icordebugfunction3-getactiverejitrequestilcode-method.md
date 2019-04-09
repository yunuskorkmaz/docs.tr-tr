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
ms.openlocfilehash: 6268019f2e65c7c9209e00c0b6065e91103980c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115888"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="86dbb-102">ICorDebugFunction3::GetActiveReJitRequestILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="86dbb-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="86dbb-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="86dbb-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="86dbb-104">Bir arabirim işaretçisi alır bir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) , etkin bir ReJIT istek IL içerir.</span><span class="sxs-lookup"><span data-stu-id="86dbb-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86dbb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86dbb-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86dbb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86dbb-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="86dbb-107">Etkin bir ReJIT istek IL işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="86dbb-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86dbb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86dbb-108">Remarks</span></span>  
 <span data-ttu-id="86dbb-109">Yöntemi bu tarafından temsil edilen varsa `ICorDebugFunction3` nesne sahip etkin bir ReJIT istek `ppReJitedILCode` , IL için bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="86dbb-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="86dbb-110">Yaygın bir durumda ise hiçbir etkin istek olup olmadığını `ppReJitedILCode` olduğu **null**.</span><span class="sxs-lookup"><span data-stu-id="86dbb-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="86dbb-111">Yürütmeyi hemen döndürür sonra ReJIT isteği etkin hale gelir [Icorprofilercallback4::getrejıtparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="86dbb-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="86dbb-112">Bunu henüz JIT olarak derlenmiş olmayabilir ve iş parçacığı hala kod'in özgün sürümünde yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="86dbb-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="86dbb-113">Profil oluşturucu çağrısı sırasında ReJIT istek devre dışı kalmadan [Icorprofilerınfo4::requestrevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="86dbb-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="86dbb-114">IL bile dönüştürüldükten sonra bir iş parçacığı JIT yeniden derlenen (ReJIT) kodda hala yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="86dbb-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86dbb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86dbb-115">Requirements</span></span>  
 <span data-ttu-id="86dbb-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86dbb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86dbb-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86dbb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86dbb-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86dbb-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="86dbb-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="86dbb-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86dbb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86dbb-120">See also</span></span>

- [<span data-ttu-id="86dbb-121">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86dbb-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="86dbb-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86dbb-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="86dbb-123">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86dbb-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)

---
title: ICorProfilerCallback9::DynamicMethodUnloaded Yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177039"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="4b87c-102">ICorProfilerCallback9::DynamicMethodUnloaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b87c-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="4b87c-103">[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenmiştir]</span><span class="sxs-lookup"><span data-stu-id="4b87c-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="4b87c-104">Dinamik bir yöntem çöp toplandığında ve daha sonra boşaltıldığında profiloluşturcucuyu not alar.</span><span class="sxs-lookup"><span data-stu-id="4b87c-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b87c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b87c-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b87c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b87c-106">Parameters</span></span>  
<span data-ttu-id="4b87c-107">[içinde]`functionId`</span><span class="sxs-lookup"><span data-stu-id="4b87c-107">[in] `functionId`</span></span>  
<span data-ttu-id="4b87c-108">Çöp toplanmış ve boşaltılmış bellek işlevinin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="4b87c-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b87c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b87c-109">Requirements</span></span>  
 <span data-ttu-id="4b87c-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b87c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b87c-111">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b87c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b87c-112">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b87c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b87c-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4b87c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b87c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b87c-114">See also</span></span>

- [<span data-ttu-id="4b87c-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b87c-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="4b87c-116">ICorProfilerCallback8.DynamicMethodJITCompilationBitmiş Yöntem</span><span class="sxs-lookup"><span data-stu-id="4b87c-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="4b87c-117">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b87c-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="4b87c-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="4b87c-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)

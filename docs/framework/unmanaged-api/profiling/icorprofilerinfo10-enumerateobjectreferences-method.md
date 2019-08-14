---
title: 'ICorProfilerInfo10:: EnumerateObjectReferences'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 4b13659f7c9909e9795caee1eace8da8092c5b9a
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973758"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="8669f-102">ICorProfilerInfo10:: EnumerateObjectReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="8669f-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>
  
 <span data-ttu-id="8669f-103">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8669f-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="8669f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8669f-104">Syntax</span></span>  
  
```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```  
  
#### <a name="parameters"></a><span data-ttu-id="8669f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8669f-105">Parameters</span></span>  

 `objectId` \
 <span data-ttu-id="8669f-106">'ndaki Başvuruların numaralandırılacağı nesne.</span><span class="sxs-lookup"><span data-stu-id="8669f-106">[in] The object to enumerate references on.</span></span>

 `callback` \
 <span data-ttu-id="8669f-107">'ndaki Nesne başvuruları ile çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="8669f-107">[in] The function that will be called with the references for the object.</span></span>

 `clientData` \
 <span data-ttu-id="8669f-108">'ndaki Profil Oluşturucu- `callback` işleve geçirilecek veriler.</span><span class="sxs-lookup"><span data-stu-id="8669f-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8669f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8669f-109">Remarks</span></span>  
 <span data-ttu-id="8669f-110">Yöntemi, başvuruları depolamak için bir diziyi önceden ayırmak yerine profil Oluşturucu için isteğe bağlı başvuruları göstermesi dışında, ObjectReferences 'a benzerdir. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) `EnumerateObjectReferences`</span><span class="sxs-lookup"><span data-stu-id="8669f-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>  

## <a name="requirements"></a><span data-ttu-id="8669f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8669f-111">Requirements</span></span>  
 <span data-ttu-id="8669f-112">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="8669f-112">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="8669f-113">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8669f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8669f-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8669f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8669f-115">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8669f-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8669f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8669f-116">See also</span></span>
- [<span data-ttu-id="8669f-117">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8669f-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)


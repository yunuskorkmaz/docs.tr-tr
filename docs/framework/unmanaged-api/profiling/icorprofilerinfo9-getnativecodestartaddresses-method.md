---
title: 'ICorProfilerInfo9:: Getnativecodestartaadresler'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5c7f11a322e4cf3ed38608e0f380dd632bc8fb6
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973692"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="2954a-102">ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi</span><span class="sxs-lookup"><span data-stu-id="2954a-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>
  
 <span data-ttu-id="2954a-103">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="2954a-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="2954a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2954a-104">Syntax</span></span>  
  
```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="2954a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2954a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2954a-106">'ndaki Yerel kod başlatma adresleri döndürülecek olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2954a-106">[in] The ID of the function whose native code start addresses should be returned.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="2954a-107">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="2954a-107">[in] The identity of the JIT-recompiled function.</span></span> 
  
 `cCodeStartAddresses` \
 <span data-ttu-id="2954a-108">'ndaki `codeStartAddresses` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="2954a-108">[in] The maximum size of the `codeStartAddresses` array.</span></span>

 `pcCodeStartAddresses` \
 <span data-ttu-id="2954a-109">dışı Kullanılabilir adreslerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="2954a-109">[out] The number of available addresses.</span></span>

 `codeStartAddresses` \
 <span data-ttu-id="2954a-110">dışı Her birinin `UINT_PTR`, belirtilen işlev için yerel gövde başlangıç adresi olan dizisi.</span><span class="sxs-lookup"><span data-stu-id="2954a-110">[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span> 

## <a name="remarks"></a><span data-ttu-id="2954a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2954a-111">Remarks</span></span>  
 <span data-ttu-id="2954a-112">Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2954a-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span> 

## <a name="requirements"></a><span data-ttu-id="2954a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2954a-113">Requirements</span></span>  
 <span data-ttu-id="2954a-114">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="2954a-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="2954a-115">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2954a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2954a-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2954a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2954a-117">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2954a-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="2954a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2954a-118">See also</span></span>
- [<span data-ttu-id="2954a-119">ICorProfilerInfo9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2954a-119">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)


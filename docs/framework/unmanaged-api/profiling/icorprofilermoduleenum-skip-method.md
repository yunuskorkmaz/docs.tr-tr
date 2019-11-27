---
title: ICorProfilerModuleEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: d8c0f69ce407638aed6475c4d84d0e032cc6a8f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435985"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="e2071-102">ICorProfilerModuleEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2071-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="e2071-103">Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="e2071-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2071-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2071-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2071-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2071-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e2071-106">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="e2071-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2071-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e2071-107">Return Value</span></span>  
 <span data-ttu-id="e2071-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2071-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e2071-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2071-109">HRESULT</span></span>|<span data-ttu-id="e2071-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2071-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2071-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2071-111">S_OK</span></span>|<span data-ttu-id="e2071-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="e2071-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="e2071-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e2071-113">S_FALSE</span></span>|<span data-ttu-id="e2071-114">Daha az sayıda öğe olmadığını belirten `celt` öğeden azı atlandı.</span><span class="sxs-lookup"><span data-stu-id="e2071-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2071-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2071-115">Remarks</span></span>  
 <span data-ttu-id="e2071-116">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="e2071-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2071-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2071-117">Requirements</span></span>  
 <span data-ttu-id="e2071-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2071-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2071-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e2071-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2071-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2071-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2071-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2071-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2071-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2071-122">See also</span></span>

- [<span data-ttu-id="e2071-123">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2071-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="e2071-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e2071-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

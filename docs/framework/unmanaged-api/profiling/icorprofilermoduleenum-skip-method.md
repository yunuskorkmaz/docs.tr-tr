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
ms.openlocfilehash: b48b782b7c8be35bfb815d72758f0bc316fb2114
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494728"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="5395a-102">ICorProfilerModuleEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5395a-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="5395a-103">Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="5395a-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5395a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5395a-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5395a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5395a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5395a-106">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="5395a-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5395a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5395a-107">Return Value</span></span>  
 <span data-ttu-id="5395a-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5395a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5395a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5395a-109">HRESULT</span></span>|<span data-ttu-id="5395a-110">Description</span><span class="sxs-lookup"><span data-stu-id="5395a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5395a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5395a-111">S_OK</span></span>|<span data-ttu-id="5395a-112">`celt`öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="5395a-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="5395a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5395a-113">S_FALSE</span></span>|<span data-ttu-id="5395a-114">Daha az öğe olmadığını `celt` belirten öğe atlandı.</span><span class="sxs-lookup"><span data-stu-id="5395a-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5395a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5395a-115">Remarks</span></span>  
 <span data-ttu-id="5395a-116">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .</span><span class="sxs-lookup"><span data-stu-id="5395a-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5395a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5395a-117">Requirements</span></span>  
 <span data-ttu-id="5395a-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5395a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5395a-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5395a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5395a-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5395a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5395a-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5395a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5395a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5395a-122">See also</span></span>

- [<span data-ttu-id="5395a-123">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5395a-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="5395a-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5395a-124">Profiling Interfaces</span></span>](profiling-interfaces.md)

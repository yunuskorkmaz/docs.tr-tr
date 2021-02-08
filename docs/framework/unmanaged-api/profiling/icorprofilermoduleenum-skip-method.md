---
description: ': ICorProfilerModuleEnum:: Skip yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4d814e5e9e369fe286b471fadc9675345cfb5b94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798972"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="906bf-103">ICorProfilerModuleEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="906bf-103">ICorProfilerModuleEnum::Skip Method</span></span>

<span data-ttu-id="906bf-104">Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="906bf-104">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906bf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="906bf-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="906bf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="906bf-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="906bf-107">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="906bf-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="906bf-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="906bf-108">Return Value</span></span>  

 <span data-ttu-id="906bf-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="906bf-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="906bf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="906bf-110">HRESULT</span></span>|<span data-ttu-id="906bf-111">Description</span><span class="sxs-lookup"><span data-stu-id="906bf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="906bf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="906bf-112">S_OK</span></span>|<span data-ttu-id="906bf-113">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="906bf-113">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="906bf-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="906bf-114">S_FALSE</span></span>|<span data-ttu-id="906bf-115">Daha az öğe olmadığını `celt` belirten öğe atlandı.</span><span class="sxs-lookup"><span data-stu-id="906bf-115">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="906bf-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="906bf-116">Remarks</span></span>  

 <span data-ttu-id="906bf-117">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .</span><span class="sxs-lookup"><span data-stu-id="906bf-117">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="906bf-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="906bf-118">Requirements</span></span>  

 <span data-ttu-id="906bf-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="906bf-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="906bf-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="906bf-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="906bf-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="906bf-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="906bf-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="906bf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906bf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="906bf-123">See also</span></span>

- [<span data-ttu-id="906bf-124">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="906bf-124">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="906bf-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="906bf-125">Profiling Interfaces</span></span>](profiling-interfaces.md)

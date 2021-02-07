---
description: ': ICorProfilerThreadEnum:: Skip yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerThreadEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: 1da191980364868ed4237fccaf7495d5417705cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736901"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="91ba8-103">ICorProfilerThreadEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91ba8-103">ICorProfilerThreadEnum::Skip Method</span></span>

<span data-ttu-id="91ba8-104">Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="91ba8-104">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ba8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91ba8-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91ba8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91ba8-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="91ba8-107">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="91ba8-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91ba8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="91ba8-108">Return Value</span></span>  

 <span data-ttu-id="91ba8-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="91ba8-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="91ba8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91ba8-110">HRESULT</span></span>|<span data-ttu-id="91ba8-111">Description</span><span class="sxs-lookup"><span data-stu-id="91ba8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91ba8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="91ba8-112">S_OK</span></span>|<span data-ttu-id="91ba8-113">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="91ba8-113">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="91ba8-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="91ba8-114">S_FALSE</span></span>|<span data-ttu-id="91ba8-115">Daha az öğe olmadığını `celt` belirten öğe atlandı.</span><span class="sxs-lookup"><span data-stu-id="91ba8-115">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91ba8-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91ba8-116">Remarks</span></span>  

 <span data-ttu-id="91ba8-117">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .</span><span class="sxs-lookup"><span data-stu-id="91ba8-117">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ba8-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91ba8-118">Requirements</span></span>  

 <span data-ttu-id="91ba8-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91ba8-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ba8-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="91ba8-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91ba8-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="91ba8-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91ba8-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ba8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ba8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91ba8-123">See also</span></span>

- [<span data-ttu-id="91ba8-124">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91ba8-124">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="91ba8-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="91ba8-125">Profiling Interfaces</span></span>](profiling-interfaces.md)

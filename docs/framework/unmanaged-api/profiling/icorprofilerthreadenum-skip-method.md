---
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
ms.openlocfilehash: 12b7b53c408388c21d7508f6591ead5ccf55936b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721185"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="f452c-102">ICorProfilerThreadEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f452c-102">ICorProfilerThreadEnum::Skip Method</span></span>

<span data-ttu-id="f452c-103">Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="f452c-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f452c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f452c-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f452c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f452c-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="f452c-106">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="f452c-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f452c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f452c-107">Return Value</span></span>  

 <span data-ttu-id="f452c-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="f452c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f452c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f452c-109">HRESULT</span></span>|<span data-ttu-id="f452c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f452c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f452c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f452c-111">S_OK</span></span>|<span data-ttu-id="f452c-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="f452c-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="f452c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f452c-113">S_FALSE</span></span>|<span data-ttu-id="f452c-114">Daha az öğe olmadığını `celt` belirten öğe atlandı.</span><span class="sxs-lookup"><span data-stu-id="f452c-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f452c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f452c-115">Remarks</span></span>  

 <span data-ttu-id="f452c-116">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .</span><span class="sxs-lookup"><span data-stu-id="f452c-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f452c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f452c-117">Requirements</span></span>  

 <span data-ttu-id="f452c-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f452c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f452c-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f452c-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f452c-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f452c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f452c-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f452c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f452c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f452c-122">See also</span></span>

- [<span data-ttu-id="f452c-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f452c-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="f452c-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f452c-124">Profiling Interfaces</span></span>](profiling-interfaces.md)

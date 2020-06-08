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
ms.openlocfilehash: 4218faf1c324175424ab20305224f7f2fa51bb7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494221"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="75faa-102">ICorProfilerThreadEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75faa-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="75faa-103">Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="75faa-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75faa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="75faa-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75faa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75faa-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="75faa-106">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="75faa-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75faa-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="75faa-107">Return Value</span></span>  
 <span data-ttu-id="75faa-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="75faa-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="75faa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75faa-109">HRESULT</span></span>|<span data-ttu-id="75faa-110">Description</span><span class="sxs-lookup"><span data-stu-id="75faa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75faa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="75faa-111">S_OK</span></span>|<span data-ttu-id="75faa-112">`celt`öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="75faa-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="75faa-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="75faa-113">S_FALSE</span></span>|<span data-ttu-id="75faa-114">Daha az öğe olmadığını `celt` belirten öğe atlandı.</span><span class="sxs-lookup"><span data-stu-id="75faa-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75faa-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75faa-115">Remarks</span></span>  
 <span data-ttu-id="75faa-116">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .</span><span class="sxs-lookup"><span data-stu-id="75faa-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75faa-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75faa-117">Requirements</span></span>  
 <span data-ttu-id="75faa-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75faa-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75faa-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="75faa-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75faa-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75faa-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75faa-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75faa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75faa-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75faa-122">See also</span></span>

- [<span data-ttu-id="75faa-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75faa-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="75faa-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="75faa-124">Profiling Interfaces</span></span>](profiling-interfaces.md)

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
ms.openlocfilehash: b08a501f7d55fbb193afd8c297ca7725348dac76
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860936"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="3c453-102">ICorProfilerThreadEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c453-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="3c453-103">Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="3c453-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c453-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c453-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c453-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c453-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3c453-106">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="3c453-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c453-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3c453-107">Return Value</span></span>  
 <span data-ttu-id="3c453-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c453-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3c453-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c453-109">HRESULT</span></span>|<span data-ttu-id="3c453-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c453-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c453-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c453-111">S_OK</span></span>|<span data-ttu-id="3c453-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="3c453-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="3c453-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3c453-113">S_FALSE</span></span>|<span data-ttu-id="3c453-114">Daha az sayıda öğe olmadığını belirten `celt` öğeden azı atlandı.</span><span class="sxs-lookup"><span data-stu-id="3c453-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c453-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c453-115">Remarks</span></span>  
 <span data-ttu-id="3c453-116">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="3c453-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c453-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c453-117">Requirements</span></span>  
 <span data-ttu-id="3c453-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c453-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c453-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3c453-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c453-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3c453-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c453-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c453-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c453-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c453-122">See also</span></span>

- [<span data-ttu-id="3c453-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c453-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="3c453-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3c453-124">Profiling Interfaces</span></span>](profiling-interfaces.md)

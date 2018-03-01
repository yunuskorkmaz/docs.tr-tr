---
title: "ICorProfilerThreadEnum::Skip Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c1840722a250dd627a5214700dca95c48aa2e8d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="bb293-102">ICorProfilerThreadEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb293-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="bb293-103">Numaralandırıcının imleç belirtilen sayıda öğeyi atlamak için geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="bb293-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb293-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb293-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb293-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb293-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bb293-106">[in] Atlanan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="bb293-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb293-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bb293-107">Return Value</span></span>  
 <span data-ttu-id="bb293-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="bb293-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bb293-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb293-109">HRESULT</span></span>|<span data-ttu-id="bb293-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb293-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb293-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb293-111">S_OK</span></span>|<span data-ttu-id="bb293-112">`celt`öğeleri atlandı.</span><span class="sxs-lookup"><span data-stu-id="bb293-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="bb293-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bb293-113">S_FALSE</span></span>|<span data-ttu-id="bb293-114">Daha az `celt` öğeleri atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb293-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb293-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb293-115">Remarks</span></span>  
 <span data-ttu-id="bb293-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumdur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="bb293-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb293-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb293-117">Requirements</span></span>  
 <span data-ttu-id="bb293-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb293-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb293-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb293-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb293-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb293-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb293-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb293-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb293-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb293-122">See Also</span></span>  
 [<span data-ttu-id="bb293-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb293-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="bb293-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bb293-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

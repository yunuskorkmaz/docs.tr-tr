---
title: "ICorProfilerThreadEnum::Skip Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f492a455165f3b49994beb3220334e2932bf214c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="da37c-102">ICorProfilerThreadEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da37c-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="da37c-103">Numaralandırıcının imleç belirtilen sayıda öğeyi atlamak için geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="da37c-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da37c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da37c-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da37c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da37c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="da37c-106">[in] Atlanan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="da37c-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da37c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="da37c-107">Return Value</span></span>  
 <span data-ttu-id="da37c-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="da37c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="da37c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da37c-109">HRESULT</span></span>|<span data-ttu-id="da37c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da37c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da37c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="da37c-111">S_OK</span></span>|<span data-ttu-id="da37c-112">`celt`öğeleri atlandı.</span><span class="sxs-lookup"><span data-stu-id="da37c-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="da37c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="da37c-113">S_FALSE</span></span>|<span data-ttu-id="da37c-114">Daha az `celt` öğeleri atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="da37c-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da37c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da37c-115">Remarks</span></span>  
 <span data-ttu-id="da37c-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumdur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="da37c-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da37c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da37c-117">Requirements</span></span>  
 <span data-ttu-id="da37c-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da37c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da37c-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da37c-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da37c-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da37c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da37c-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da37c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da37c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da37c-122">See Also</span></span>  
 [<span data-ttu-id="da37c-123">Icorprofilerthreadenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="da37c-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="da37c-124">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="da37c-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

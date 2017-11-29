---
title: "ICorDebugInternalFrame2::IsCloserToLeaf Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60e63800ade5fb0d4a222d80ebfe43c3d84c2815
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="06afa-102">ICorDebugInternalFrame2::IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06afa-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="06afa-103">Denetler olup olmadığını `this` iç kare belirtilen Icordebugframe nesne yaprak daha yakın olur.</span><span class="sxs-lookup"><span data-stu-id="06afa-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06afa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06afa-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06afa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06afa-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="06afa-106">[in] Karşılaştırma için bir işaretçi `ICorDebugFrame` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="06afa-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="06afa-107">[out] `true` varsa `this` iç çerçeve yaprak tarafından belirtilen çerçeve daha yakından `pFrameToCompare`; Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="06afa-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06afa-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06afa-108">Return Value</span></span>  
 <span data-ttu-id="06afa-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="06afa-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="06afa-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06afa-110">HRESULT</span></span>|<span data-ttu-id="06afa-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06afa-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06afa-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="06afa-112">S_OK</span></span>|<span data-ttu-id="06afa-113">Karşılaştırma başarıyla gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="06afa-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="06afa-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="06afa-114">E_FAIL</span></span>|<span data-ttu-id="06afa-115">Karşılaştırma gerçekleştirilemedi.</span><span class="sxs-lookup"><span data-stu-id="06afa-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="06afa-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="06afa-116">E_INVALIDARG</span></span>|<span data-ttu-id="06afa-117">`pFrameToCompare`veya `pIsCloser` null.</span><span class="sxs-lookup"><span data-stu-id="06afa-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06afa-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06afa-118">Remarks</span></span>  
 <span data-ttu-id="06afa-119">`IsCloserToLeaf`diğer çerçeveler yığında ile iç çerçeveler Interleaving ilkesini uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06afa-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06afa-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06afa-120">Requirements</span></span>  
 <span data-ttu-id="06afa-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06afa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06afa-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06afa-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06afa-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06afa-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06afa-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06afa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06afa-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06afa-125">See Also</span></span>  
 [<span data-ttu-id="06afa-126">Icordebugınternalframe2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="06afa-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="06afa-127">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="06afa-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="06afa-128">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="06afa-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

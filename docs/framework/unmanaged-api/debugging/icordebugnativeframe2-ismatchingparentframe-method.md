---
title: "ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc2d8eacb05e861290ad19a34c261943dc2959a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="28f16-102">ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28f16-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="28f16-103">Belirtilen çerçeve geçerli çerçevenin üst olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="28f16-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28f16-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28f16-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28f16-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28f16-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="28f16-106">[in] Üst durumu için değerlendirmek istediğiniz çerçeve nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="28f16-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="28f16-107">[out] `true` varsa `pPotentialParentFrame` geçerli çerçevenin üst; Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="28f16-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28f16-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="28f16-108">Return Value</span></span>  
 <span data-ttu-id="28f16-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="28f16-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="28f16-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28f16-110">HRESULT</span></span>|<span data-ttu-id="28f16-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28f16-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28f16-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="28f16-112">S_OK</span></span>|<span data-ttu-id="28f16-113">Üst durumu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="28f16-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="28f16-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28f16-114">E_FAIL</span></span>|<span data-ttu-id="28f16-115">Üst durumu döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="28f16-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="28f16-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="28f16-116">E_INVALIDARG</span></span>|<span data-ttu-id="28f16-117">`pPotentialParentFrame`veya `pIsParent` null.</span><span class="sxs-lookup"><span data-stu-id="28f16-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="28f16-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="28f16-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28f16-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28f16-119">Remarks</span></span>  
 <span data-ttu-id="28f16-120">`IsMatchingParentFrame`döndürür `true` yöntemine geçirdiğiniz çerçeve nesnesi yöntemi çağrıldı çerçeve nesnenin üst olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="28f16-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="28f16-121">Belirtilen çerçeve alt olmayan bir çerçeve yöntemini çağırırsanız, hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="28f16-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28f16-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28f16-122">Requirements</span></span>  
 <span data-ttu-id="28f16-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28f16-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28f16-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28f16-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28f16-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28f16-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28f16-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28f16-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f16-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28f16-127">See Also</span></span>  
 [<span data-ttu-id="28f16-128">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28f16-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="28f16-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="28f16-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="28f16-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="28f16-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

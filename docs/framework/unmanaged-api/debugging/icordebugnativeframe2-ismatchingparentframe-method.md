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
ms.openlocfilehash: e261f4cb43843ec61ec6cbd1609e6967a4a38a82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="1b187-102">ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b187-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="1b187-103">Belirtilen çerçeve geçerli çerçevenin üst olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1b187-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b187-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b187-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b187-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b187-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="1b187-106">[in] Üst durumu için değerlendirmek istediğiniz çerçeve nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1b187-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="1b187-107">[out] `true` varsa `pPotentialParentFrame` geçerli çerçevenin üst; Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="1b187-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b187-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1b187-108">Return Value</span></span>  
 <span data-ttu-id="1b187-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="1b187-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1b187-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b187-110">HRESULT</span></span>|<span data-ttu-id="1b187-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b187-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b187-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b187-112">S_OK</span></span>|<span data-ttu-id="1b187-113">Üst durumu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1b187-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="1b187-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b187-114">E_FAIL</span></span>|<span data-ttu-id="1b187-115">Üst durumu döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="1b187-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="1b187-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1b187-116">E_INVALIDARG</span></span>|<span data-ttu-id="1b187-117">`pPotentialParentFrame`veya `pIsParent` null.</span><span class="sxs-lookup"><span data-stu-id="1b187-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1b187-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="1b187-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b187-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b187-119">Remarks</span></span>  
 <span data-ttu-id="1b187-120">`IsMatchingParentFrame`döndürür `true` yöntemine geçirdiğiniz çerçeve nesnesi yöntemi çağrıldı çerçeve nesnenin üst olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="1b187-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="1b187-121">Belirtilen çerçeve alt olmayan bir çerçeve yöntemini çağırırsanız, hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b187-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b187-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b187-122">Requirements</span></span>  
 <span data-ttu-id="1b187-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b187-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b187-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b187-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b187-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b187-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b187-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b187-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b187-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b187-127">See Also</span></span>  
 [<span data-ttu-id="1b187-128">Icordebugnativeframe2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b187-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="1b187-129">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b187-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1b187-130">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1b187-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

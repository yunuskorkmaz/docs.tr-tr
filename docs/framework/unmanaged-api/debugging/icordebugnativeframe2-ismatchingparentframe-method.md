---
title: ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e215cf4f6d6c3cfde3fa723ecae67aa77e189917
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757063"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="fd868-102">ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd868-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="fd868-103">Belirtilen çerçeve geçerli çerçevenin üst olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fd868-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd868-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd868-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd868-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd868-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="fd868-106">[in] Üst durumu için değerlendirmek istediğiniz çerçeve nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd868-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="fd868-107">[out] `true` varsa `pPotentialParentFrame` geçerli çerçevenin üst; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="fd868-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd868-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd868-108">Return Value</span></span>  
 <span data-ttu-id="fd868-109">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="fd868-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fd868-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd868-110">HRESULT</span></span>|<span data-ttu-id="fd868-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd868-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd868-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd868-112">S_OK</span></span>|<span data-ttu-id="fd868-113">Üst durumu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fd868-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="fd868-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd868-114">E_FAIL</span></span>|<span data-ttu-id="fd868-115">Üst durumu döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="fd868-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="fd868-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fd868-116">E_INVALIDARG</span></span>|<span data-ttu-id="fd868-117">`pPotentialParentFrame` veya `pIsParent` null.</span><span class="sxs-lookup"><span data-stu-id="fd868-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="fd868-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="fd868-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd868-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd868-119">Remarks</span></span>  
 <span data-ttu-id="fd868-120">`IsMatchingParentFrame` döndürür `true` yöntemine geçirdiğiniz çerçeve nesnesi yöntemi çağrıldı çerçevesi nesnenin üst olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="fd868-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="fd868-121">Belirtilen çerçeve alt düğümü değil bir karede yöntem çağırırsanız, bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd868-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd868-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd868-122">Requirements</span></span>  
 <span data-ttu-id="fd868-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd868-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd868-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd868-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd868-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd868-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd868-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd868-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd868-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd868-127">See also</span></span>

- [<span data-ttu-id="fd868-128">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd868-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="fd868-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fd868-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fd868-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fd868-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

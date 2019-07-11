---
title: ICorDebugNativeFrame2::IsChild Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550d25e995bdfe010fb1aa664a7c9882a775f4d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757165"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="9ab7e-102">ICorDebugNativeFrame2::IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ab7e-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="9ab7e-103">Geçerli çerçeve bir alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ab7e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ab7e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ab7e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ab7e-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="9ab7e-106">[out] Geçerli çerçeve bir alt çerçeve olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ab7e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9ab7e-107">Return Value</span></span>  
 <span data-ttu-id="9ab7e-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9ab7e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ab7e-109">HRESULT</span></span>|<span data-ttu-id="9ab7e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ab7e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ab7e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ab7e-111">S_OK</span></span>|<span data-ttu-id="9ab7e-112">Alt durumu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="9ab7e-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ab7e-113">E_FAIL</span></span>|<span data-ttu-id="9ab7e-114">Alt öğe durumuna döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="9ab7e-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9ab7e-115">E_INVALIDARG</span></span>|<span data-ttu-id="9ab7e-116">`pIsChild` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9ab7e-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="9ab7e-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ab7e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ab7e-118">Remarks</span></span>  
 <span data-ttu-id="9ab7e-119">`IsChild` Yöntemi döndürür `true` yöntem çağırmanızı çerçeve nesnesi başka bir çerçevenin bir alt olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="9ab7e-120">Bu durumda kullanın [Ismatchingparentframe](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) çerçeve üst olup olmadığını denetlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ab7e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ab7e-121">Requirements</span></span>  
 <span data-ttu-id="9ab7e-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ab7e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ab7e-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ab7e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ab7e-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ab7e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ab7e-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ab7e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab7e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ab7e-126">See also</span></span>

- [<span data-ttu-id="9ab7e-127">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ab7e-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="9ab7e-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9ab7e-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9ab7e-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9ab7e-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

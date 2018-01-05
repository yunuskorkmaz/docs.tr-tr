---
title: "ICorDebugNativeFrame2::IsChild Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsChild Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 267bc2fcd03786bfceb218dd0218ffa7006f8fa7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="29c20-102">ICorDebugNativeFrame2::IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29c20-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="29c20-103">Geçerli çerçeve alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="29c20-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c20-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29c20-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29c20-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29c20-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="29c20-106">[out] Geçerli çerçeve alt çerçeve olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="29c20-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29c20-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29c20-107">Return Value</span></span>  
 <span data-ttu-id="29c20-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="29c20-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="29c20-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29c20-109">HRESULT</span></span>|<span data-ttu-id="29c20-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29c20-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29c20-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="29c20-111">S_OK</span></span>|<span data-ttu-id="29c20-112">Alt durum başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="29c20-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="29c20-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29c20-113">E_FAIL</span></span>|<span data-ttu-id="29c20-114">Alt durum döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="29c20-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="29c20-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="29c20-115">E_INVALIDARG</span></span>|<span data-ttu-id="29c20-116">`pIsChild`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="29c20-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="29c20-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="29c20-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29c20-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29c20-118">Remarks</span></span>  
 <span data-ttu-id="29c20-119">`IsChild` Yöntemi döndürür `true` üzerinde yöntemi çağırmanız çerçeve nesnesi başka bir çerçeve alt olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="29c20-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="29c20-120">Bu durumda kullanın [Ismatchingparentframe](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) yöntemi bir çerçeve üst olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="29c20-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c20-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29c20-121">Requirements</span></span>  
 <span data-ttu-id="29c20-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c20-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c20-123">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29c20-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29c20-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29c20-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29c20-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29c20-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c20-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29c20-126">See Also</span></span>  
 [<span data-ttu-id="29c20-127">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29c20-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="29c20-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="29c20-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="29c20-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="29c20-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

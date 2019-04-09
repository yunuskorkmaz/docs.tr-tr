---
title: ICorDebugInternalFrame2::IsCloserToLeaf Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30a9d26283d4f544bdd865e40cfc1c1c625ae462
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120906"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="35a8e-102">ICorDebugInternalFrame2::IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35a8e-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="35a8e-103">Denetler olmadığını `this` iç çerçeve belirtilen Icordebugframe nesneden yaprağa yakın.</span><span class="sxs-lookup"><span data-stu-id="35a8e-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35a8e-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35a8e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35a8e-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="35a8e-106">[in] Karşılaştırma için bir işaretçi `ICorDebugFrame` nesne.</span><span class="sxs-lookup"><span data-stu-id="35a8e-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="35a8e-107">[out] `true` varsa `this` iç çerçeve yaprağa tarafından belirtilen çerçeve daha yakından `pFrameToCompare`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="35a8e-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35a8e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="35a8e-108">Return Value</span></span>  
 <span data-ttu-id="35a8e-109">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="35a8e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="35a8e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35a8e-110">HRESULT</span></span>|<span data-ttu-id="35a8e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35a8e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35a8e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="35a8e-112">S_OK</span></span>|<span data-ttu-id="35a8e-113">Karşılaştırma başarıyla gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="35a8e-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="35a8e-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="35a8e-114">E_FAIL</span></span>|<span data-ttu-id="35a8e-115">Karşılaştırma gerçekleştirilemedi.</span><span class="sxs-lookup"><span data-stu-id="35a8e-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="35a8e-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="35a8e-116">E_INVALIDARG</span></span>|`pFrameToCompare` <span data-ttu-id="35a8e-117">veya `pIsCloser` null.</span><span class="sxs-lookup"><span data-stu-id="35a8e-117">or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35a8e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35a8e-118">Remarks</span></span>  
 `IsCloserToLeaf` <span data-ttu-id="35a8e-119">İç çerçeveler yığında diğer çerçevelerle Interleaving ilkesini uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35a8e-119">can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a8e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35a8e-120">Requirements</span></span>  
 <span data-ttu-id="35a8e-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35a8e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a8e-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35a8e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35a8e-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35a8e-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="35a8e-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="35a8e-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35a8e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35a8e-125">See also</span></span>

- [<span data-ttu-id="35a8e-126">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35a8e-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="35a8e-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="35a8e-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="35a8e-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="35a8e-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

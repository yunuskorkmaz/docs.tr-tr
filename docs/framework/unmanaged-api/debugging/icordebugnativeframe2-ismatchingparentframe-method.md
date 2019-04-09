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
ms.openlocfilehash: 0a553f2cbac6110e82803e6d0dd872cfaa15d773
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099930"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="9e96d-102">ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e96d-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="9e96d-103">Belirtilen çerçeve geçerli çerçevenin üst olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9e96d-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e96d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e96d-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e96d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e96d-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="9e96d-106">[in] Üst durumu için değerlendirmek istediğiniz çerçeve nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9e96d-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="9e96d-107">[out] `true` varsa `pPotentialParentFrame` geçerli çerçevenin üst; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="9e96d-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e96d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e96d-108">Return Value</span></span>  
 <span data-ttu-id="9e96d-109">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="9e96d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9e96d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e96d-110">HRESULT</span></span>|<span data-ttu-id="9e96d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e96d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e96d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e96d-112">S_OK</span></span>|<span data-ttu-id="9e96d-113">Üst durumu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9e96d-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="9e96d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e96d-114">E_FAIL</span></span>|<span data-ttu-id="9e96d-115">Üst durumu döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="9e96d-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="9e96d-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9e96d-116">E_INVALIDARG</span></span>|`pPotentialParentFrame` <span data-ttu-id="9e96d-117">veya `pIsParent` null.</span><span class="sxs-lookup"><span data-stu-id="9e96d-117">or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9e96d-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="9e96d-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e96d-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e96d-119">Remarks</span></span>  
 `IsMatchingParentFrame` <span data-ttu-id="9e96d-120">döndürür `true` yöntemine geçirdiğiniz çerçeve nesnesi yöntemi çağrıldı çerçevesi nesnenin üst olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="9e96d-120">returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="9e96d-121">Belirtilen çerçeve alt düğümü değil bir karede yöntem çağırırsanız, bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e96d-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e96d-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e96d-122">Requirements</span></span>  
 <span data-ttu-id="9e96d-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e96d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e96d-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e96d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e96d-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e96d-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9e96d-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9e96d-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e96d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e96d-127">See also</span></span>

- [<span data-ttu-id="9e96d-128">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e96d-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="9e96d-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e96d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9e96d-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9e96d-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

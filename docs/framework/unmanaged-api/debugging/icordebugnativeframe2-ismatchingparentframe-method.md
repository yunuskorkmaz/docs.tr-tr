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
ms.openlocfilehash: 5bcced647af6436bd8f5b1f3779d9368b6173d11
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213042"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="41c7b-102">ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41c7b-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="41c7b-103">Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="41c7b-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c7b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41c7b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41c7b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41c7b-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="41c7b-106">'ndaki Üst durum için değerlendirmek istediğiniz çerçeve nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="41c7b-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="41c7b-107">[out] `true` `pPotentialParentFrame`Geçerli çerçevenin üst öğesi ise, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="41c7b-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41c7b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41c7b-108">Return Value</span></span>  
 <span data-ttu-id="41c7b-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="41c7b-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="41c7b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41c7b-110">HRESULT</span></span>|<span data-ttu-id="41c7b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41c7b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41c7b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="41c7b-112">S_OK</span></span>|<span data-ttu-id="41c7b-113">Üst durum başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="41c7b-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="41c7b-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41c7b-114">E_FAIL</span></span>|<span data-ttu-id="41c7b-115">Üst durum döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="41c7b-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="41c7b-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="41c7b-116">E_INVALIDARG</span></span>|<span data-ttu-id="41c7b-117">`pPotentialParentFrame`ya da `pIsParent` null.</span><span class="sxs-lookup"><span data-stu-id="41c7b-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="41c7b-118">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="41c7b-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41c7b-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41c7b-119">Remarks</span></span>  
 <span data-ttu-id="41c7b-120">`IsMatchingParentFrame``true`yöntemine geçirdiğiniz çerçeve nesnesinin, yöntemin çağrıldığı çerçeve nesnesinin üst öğesi olup olmadığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="41c7b-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="41c7b-121">Yöntemi belirtilen çerçevenin alt öğesi olmayan bir çerçevede çağırırsanız, bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="41c7b-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c7b-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41c7b-122">Requirements</span></span>  
 <span data-ttu-id="41c7b-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c7b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c7b-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41c7b-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41c7b-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="41c7b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41c7b-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c7b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c7b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41c7b-127">See also</span></span>

- [<span data-ttu-id="41c7b-128">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41c7b-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="41c7b-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="41c7b-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="41c7b-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="41c7b-130">Debugging</span></span>](index.md)

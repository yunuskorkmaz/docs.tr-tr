---
description: ': ICorDebugNativeFrame2:: IsMatchingParentFrame yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6dff1cb7f5205ad742ac4b886f72938dd28bd88f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722210"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="22860-103">ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22860-103">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>

<span data-ttu-id="22860-104">Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="22860-104">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22860-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22860-105">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22860-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22860-106">Parameters</span></span>  

 `pPotentialParentFrame`  
 <span data-ttu-id="22860-107">'ndaki Üst durum için değerlendirmek istediğiniz çerçeve nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22860-107">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="22860-108">[out] `true` `pPotentialParentFrame` Geçerli çerçevenin üst öğesi ise, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="22860-108">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22860-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="22860-109">Return Value</span></span>  

 <span data-ttu-id="22860-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="22860-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="22860-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22860-111">HRESULT</span></span>|<span data-ttu-id="22860-112">Description</span><span class="sxs-lookup"><span data-stu-id="22860-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22860-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="22860-113">S_OK</span></span>|<span data-ttu-id="22860-114">Üst durum başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="22860-114">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="22860-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22860-115">E_FAIL</span></span>|<span data-ttu-id="22860-116">Üst durum döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="22860-116">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="22860-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="22860-117">E_INVALIDARG</span></span>|<span data-ttu-id="22860-118">`pPotentialParentFrame` ya da `pIsParent` null.</span><span class="sxs-lookup"><span data-stu-id="22860-118">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="22860-119">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="22860-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22860-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22860-120">Remarks</span></span>  

 <span data-ttu-id="22860-121">`IsMatchingParentFrame``true`yöntemine geçirdiğiniz çerçeve nesnesinin, yöntemin çağrıldığı çerçeve nesnesinin üst öğesi olup olmadığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="22860-121">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="22860-122">Yöntemi belirtilen çerçevenin alt öğesi olmayan bir çerçevede çağırırsanız, bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="22860-122">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22860-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22860-123">Requirements</span></span>  

 <span data-ttu-id="22860-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22860-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22860-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="22860-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22860-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="22860-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22860-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22860-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22860-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22860-128">See also</span></span>

- [<span data-ttu-id="22860-129">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22860-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="22860-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="22860-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="22860-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="22860-131">Debugging</span></span>](index.md)

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
ms.openlocfilehash: aeaa706ef35413a728f8b254cd325f0bcc83acd1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792707"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="26093-102">ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26093-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="26093-103">Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="26093-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26093-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26093-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26093-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26093-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="26093-106">'ndaki Üst durum için değerlendirmek istediğiniz çerçeve nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26093-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="26093-107">[out] `pPotentialParentFrame` geçerli çerçevenin üst öğesi ise `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="26093-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26093-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="26093-108">Return Value</span></span>  
 <span data-ttu-id="26093-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="26093-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="26093-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26093-110">HRESULT</span></span>|<span data-ttu-id="26093-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26093-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26093-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="26093-112">S_OK</span></span>|<span data-ttu-id="26093-113">Üst durum başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="26093-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="26093-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26093-114">E_FAIL</span></span>|<span data-ttu-id="26093-115">Üst durum döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="26093-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="26093-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="26093-116">E_INVALIDARG</span></span>|<span data-ttu-id="26093-117">`pPotentialParentFrame` veya `pIsParent` null.</span><span class="sxs-lookup"><span data-stu-id="26093-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="26093-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="26093-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26093-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26093-119">Remarks</span></span>  
 <span data-ttu-id="26093-120">`IsMatchingParentFrame`, yöntemine geçirdiğiniz çerçeve nesnesinin, yöntemin çağrıldığı üst öğesi ise `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="26093-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="26093-121">Yöntemi belirtilen çerçevenin alt öğesi olmayan bir çerçevede çağırırsanız, bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="26093-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26093-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26093-122">Requirements</span></span>  
 <span data-ttu-id="26093-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26093-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26093-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="26093-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26093-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="26093-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26093-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26093-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26093-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26093-127">See also</span></span>

- [<span data-ttu-id="26093-128">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26093-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="26093-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26093-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="26093-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="26093-130">Debugging</span></span>](index.md)

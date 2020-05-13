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
ms.openlocfilehash: 4a01ccd4e5cb9aadc6a693b2c6ceaff31c114bbc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209896"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="0c523-102">ICorDebugInternalFrame2::IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c523-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="0c523-103">`this`İç karenin belirtilen ICorDebugFrame nesnesinden daha yakın olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="0c523-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c523-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c523-104">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c523-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c523-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="0c523-106">'ndaki Karşılaştırma nesnesine yönelik bir işaretçi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="0c523-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="0c523-107">[out] `true` `this`iç çerçeve, tarafından belirtilen çerçeveden daha yakınsa `pFrameToCompare` , aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="0c523-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c523-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0c523-108">Return Value</span></span>  
 <span data-ttu-id="0c523-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c523-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0c523-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c523-110">HRESULT</span></span>|<span data-ttu-id="0c523-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c523-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c523-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c523-112">S_OK</span></span>|<span data-ttu-id="0c523-113">Karşılaştırma başarıyla gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="0c523-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="0c523-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c523-114">E_FAIL</span></span>|<span data-ttu-id="0c523-115">Karşılaştırma gerçekleştirilemedi.</span><span class="sxs-lookup"><span data-stu-id="0c523-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="0c523-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0c523-116">E_INVALIDARG</span></span>|<span data-ttu-id="0c523-117">`pFrameToCompare`ya da `pIsCloser` null.</span><span class="sxs-lookup"><span data-stu-id="0c523-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c523-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c523-118">Remarks</span></span>  
 <span data-ttu-id="0c523-119">`IsCloserToLeaf`yığındaki diğer çerçevelerle iç çerçeveler Ekleme ilkesi uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c523-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c523-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c523-120">Requirements</span></span>  
 <span data-ttu-id="0c523-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c523-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c523-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c523-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c523-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0c523-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c523-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c523-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c523-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c523-125">See also</span></span>

- [<span data-ttu-id="0c523-126">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c523-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="0c523-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0c523-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0c523-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0c523-128">Debugging</span></span>](index.md)

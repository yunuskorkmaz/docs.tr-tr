---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugInternalFrame2:: ıclosertoyaprak yöntemi'
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
ms.openlocfilehash: d773f8670f600a5bcd2a8dad7f23fe243195957c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801286"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="1f7fd-103">ICorDebugInternalFrame2::IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f7fd-103">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>

<span data-ttu-id="1f7fd-104">`this`İç karenin belirtilen ICorDebugFrame nesnesinden daha yakın olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1f7fd-104">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f7fd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f7fd-105">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f7fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f7fd-106">Parameters</span></span>  

 `pFrameToCompare`  
 <span data-ttu-id="1f7fd-107">'ndaki Karşılaştırma nesnesine yönelik bir işaretçi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="1f7fd-107">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="1f7fd-108">[out] `true` `this` iç çerçeve, tarafından belirtilen çerçeveden daha yakınsa `pFrameToCompare` , aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="1f7fd-108">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f7fd-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f7fd-109">Return Value</span></span>  

 <span data-ttu-id="1f7fd-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f7fd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1f7fd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f7fd-111">HRESULT</span></span>|<span data-ttu-id="1f7fd-112">Description</span><span class="sxs-lookup"><span data-stu-id="1f7fd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f7fd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f7fd-113">S_OK</span></span>|<span data-ttu-id="1f7fd-114">Karşılaştırma başarıyla gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="1f7fd-114">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="1f7fd-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f7fd-115">E_FAIL</span></span>|<span data-ttu-id="1f7fd-116">Karşılaştırma gerçekleştirilemedi.</span><span class="sxs-lookup"><span data-stu-id="1f7fd-116">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="1f7fd-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1f7fd-117">E_INVALIDARG</span></span>|<span data-ttu-id="1f7fd-118">`pFrameToCompare` ya da `pIsCloser` null.</span><span class="sxs-lookup"><span data-stu-id="1f7fd-118">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f7fd-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f7fd-119">Remarks</span></span>  

 <span data-ttu-id="1f7fd-120">`IsCloserToLeaf` yığındaki diğer çerçevelerle iç çerçeveler Ekleme ilkesi uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f7fd-120">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f7fd-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f7fd-121">Requirements</span></span>  

 <span data-ttu-id="1f7fd-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f7fd-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f7fd-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1f7fd-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f7fd-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1f7fd-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f7fd-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f7fd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f7fd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f7fd-126">See also</span></span>

- [<span data-ttu-id="1f7fd-127">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f7fd-127">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="1f7fd-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1f7fd-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1f7fd-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1f7fd-129">Debugging</span></span>](index.md)

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
ms.openlocfilehash: 0d65849aba08c7d143a6977e7dfb8cff85274a64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695575"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="ffdb9-102">ICorDebugNativeFrame2::IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffdb9-102">ICorDebugNativeFrame2::IsChild Method</span></span>

<span data-ttu-id="ffdb9-103">Geçerli çerçevenin bir alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdb9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ffdb9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffdb9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ffdb9-105">Parameters</span></span>  

 `pIsChild`  
 <span data-ttu-id="ffdb9-106">dışı Geçerli çerçevenin bir alt çerçeve olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffdb9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ffdb9-107">Return Value</span></span>  

 <span data-ttu-id="ffdb9-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ffdb9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffdb9-109">HRESULT</span></span>|<span data-ttu-id="ffdb9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffdb9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffdb9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffdb9-111">S_OK</span></span>|<span data-ttu-id="ffdb9-112">Alt durum başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="ffdb9-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffdb9-113">E_FAIL</span></span>|<span data-ttu-id="ffdb9-114">Alt durum döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="ffdb9-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ffdb9-115">E_INVALIDARG</span></span>|<span data-ttu-id="ffdb9-116">`pIsChild` null.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ffdb9-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="ffdb9-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffdb9-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffdb9-118">Remarks</span></span>  

 <span data-ttu-id="ffdb9-119">Yöntemi, `IsChild` `true` yöntemi çağırdığınız çerçeve nesnesi başka bir çerçevenin alt öğesi ise döndürür.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="ffdb9-120">Bu durumda, bir çerçevenin üst öğesi olup olmadığını denetlemek için [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-120">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffdb9-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffdb9-121">Requirements</span></span>  

 <span data-ttu-id="ffdb9-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffdb9-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffdb9-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ffdb9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffdb9-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ffdb9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffdb9-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffdb9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdb9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffdb9-126">See also</span></span>

- [<span data-ttu-id="ffdb9-127">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffdb9-127">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="ffdb9-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ffdb9-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ffdb9-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ffdb9-129">Debugging</span></span>](index.md)

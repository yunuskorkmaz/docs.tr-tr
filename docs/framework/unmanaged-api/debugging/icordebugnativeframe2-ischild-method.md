---
description: 'Daha fazla bilgi edinin: ICorDebugNativeFrame2:: IsChild yöntemi'
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
ms.openlocfilehash: 7c698c5a49ee445b4ba9c591c96f700f86a86c32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722301"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="0e07e-103">ICorDebugNativeFrame2::IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e07e-103">ICorDebugNativeFrame2::IsChild Method</span></span>

<span data-ttu-id="0e07e-104">Geçerli çerçevenin bir alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="0e07e-104">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e07e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e07e-105">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e07e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e07e-106">Parameters</span></span>  

 `pIsChild`  
 <span data-ttu-id="0e07e-107">dışı Geçerli çerçevenin bir alt çerçeve olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="0e07e-107">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e07e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e07e-108">Return Value</span></span>  

 <span data-ttu-id="0e07e-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e07e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0e07e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e07e-110">HRESULT</span></span>|<span data-ttu-id="0e07e-111">Description</span><span class="sxs-lookup"><span data-stu-id="0e07e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e07e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e07e-112">S_OK</span></span>|<span data-ttu-id="0e07e-113">Alt durum başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0e07e-113">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="0e07e-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e07e-114">E_FAIL</span></span>|<span data-ttu-id="0e07e-115">Alt durum döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="0e07e-115">The child status could not be returned.</span></span>|  
|<span data-ttu-id="0e07e-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0e07e-116">E_INVALIDARG</span></span>|<span data-ttu-id="0e07e-117">`pIsChild` null.</span><span class="sxs-lookup"><span data-stu-id="0e07e-117">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0e07e-118">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="0e07e-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e07e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e07e-119">Remarks</span></span>  

 <span data-ttu-id="0e07e-120">Yöntemi, `IsChild` `true` yöntemi çağırdığınız çerçeve nesnesi başka bir çerçevenin alt öğesi ise döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e07e-120">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="0e07e-121">Bu durumda, bir çerçevenin üst öğesi olup olmadığını denetlemek için [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e07e-121">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e07e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e07e-122">Requirements</span></span>  

 <span data-ttu-id="0e07e-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e07e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e07e-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0e07e-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e07e-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0e07e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e07e-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e07e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e07e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e07e-127">See also</span></span>

- [<span data-ttu-id="0e07e-128">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e07e-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="0e07e-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0e07e-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0e07e-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0e07e-130">Debugging</span></span>](index.md)

---
title: ICorDebugInternalFrame2::GetFrameAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f44f0707892197398e4638a5e6d037fba7c8fc71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="34e2c-102">ICorDebugInternalFrame2::GetFrameAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="34e2c-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="34e2c-103">İç çerçeve yığını adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="34e2c-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34e2c-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34e2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34e2c-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="34e2c-106">[out] İşaretçi `CORDB_ADDRESS` iç çerçevesi için.</span><span class="sxs-lookup"><span data-stu-id="34e2c-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34e2c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34e2c-107">Return Value</span></span>  
 <span data-ttu-id="34e2c-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="34e2c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="34e2c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34e2c-109">HRESULT</span></span>|<span data-ttu-id="34e2c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34e2c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34e2c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="34e2c-111">S_OK</span></span>|<span data-ttu-id="34e2c-112">İç çerçeve adresini başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="34e2c-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="34e2c-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34e2c-113">E_FAIL</span></span>|<span data-ttu-id="34e2c-114">İç çerçeve adresini döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="34e2c-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="34e2c-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="34e2c-115">E_INVALIDARG</span></span>|<span data-ttu-id="34e2c-116">`pAddress`olan `null`.</span><span class="sxs-lookup"><span data-stu-id="34e2c-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34e2c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34e2c-117">Remarks</span></span>  
 <span data-ttu-id="34e2c-118">Döndürülen değerin `pAddress` iç çerçeve diğer çerçeveler yığında göreli konumunu belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34e2c-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="34e2c-119">Hatta IA-64 tabanlı bilgisayarlar iç çerçeve yalnızca yığın üzerinde bulunacağı ve yedekleme deposu için karşılık gelen bir işaretçi yok.</span><span class="sxs-lookup"><span data-stu-id="34e2c-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34e2c-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34e2c-120">Requirements</span></span>  
 <span data-ttu-id="34e2c-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34e2c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34e2c-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34e2c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34e2c-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34e2c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34e2c-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34e2c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e2c-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34e2c-125">See Also</span></span>  
 [<span data-ttu-id="34e2c-126">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34e2c-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="34e2c-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="34e2c-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="34e2c-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="34e2c-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

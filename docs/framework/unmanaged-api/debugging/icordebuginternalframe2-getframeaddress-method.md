---
title: ICorDebugInternalFrame2::GetFrameAddress Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3293c3b0d5fa4615c351949afdb1acf8cd560b5e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480721"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="361b2-102">ICorDebugInternalFrame2::GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="361b2-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="361b2-103">İç çerçevenin yığın adresi döndürür.</span><span class="sxs-lookup"><span data-stu-id="361b2-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="361b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="361b2-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="361b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="361b2-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="361b2-106">[out] İşaretçi `CORDB_ADDRESS` iç çerçeve için.</span><span class="sxs-lookup"><span data-stu-id="361b2-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="361b2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="361b2-107">Return Value</span></span>  
 <span data-ttu-id="361b2-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="361b2-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="361b2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="361b2-109">HRESULT</span></span>|<span data-ttu-id="361b2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="361b2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="361b2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="361b2-111">S_OK</span></span>|<span data-ttu-id="361b2-112">İç çerçeve adresini başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="361b2-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="361b2-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="361b2-113">E_FAIL</span></span>|<span data-ttu-id="361b2-114">İç çerçeve adresini döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="361b2-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="361b2-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="361b2-115">E_INVALIDARG</span></span>|<span data-ttu-id="361b2-116">`pAddress` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="361b2-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="361b2-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="361b2-117">Remarks</span></span>  
 <span data-ttu-id="361b2-118">Döndürülen değer `pAddress` iç çerçevenin yığın üzerinde diğer çerçeveler göreli konumunu belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="361b2-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="361b2-119">IA-64 tabanlı bilgisayarlarda bile şirket iç çerçeve yalnızca yığında yer alan ve bir yedekleme deposu için karşılık gelen bir işaretçi yok.</span><span class="sxs-lookup"><span data-stu-id="361b2-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="361b2-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="361b2-120">Requirements</span></span>  
 <span data-ttu-id="361b2-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="361b2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="361b2-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="361b2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="361b2-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="361b2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="361b2-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="361b2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="361b2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="361b2-125">See also</span></span>
- [<span data-ttu-id="361b2-126">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="361b2-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="361b2-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="361b2-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="361b2-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="361b2-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

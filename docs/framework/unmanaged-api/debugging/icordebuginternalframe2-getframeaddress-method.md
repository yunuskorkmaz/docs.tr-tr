---
title: ICorDebugInternalFrame2::GetFrameAddress Metodu
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
ms.openlocfilehash: d088aaaaa80ee3513a37ea0345d720832504c005
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421154"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="8911e-102">ICorDebugInternalFrame2::GetFrameAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="8911e-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="8911e-103">İç çerçeve yığını adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8911e-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8911e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8911e-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8911e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8911e-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="8911e-106">[out] İşaretçi `CORDB_ADDRESS` iç çerçevesi için.</span><span class="sxs-lookup"><span data-stu-id="8911e-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8911e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8911e-107">Return Value</span></span>  
 <span data-ttu-id="8911e-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8911e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8911e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8911e-109">HRESULT</span></span>|<span data-ttu-id="8911e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8911e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8911e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8911e-111">S_OK</span></span>|<span data-ttu-id="8911e-112">İç çerçeve adresini başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8911e-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="8911e-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8911e-113">E_FAIL</span></span>|<span data-ttu-id="8911e-114">İç çerçeve adresini döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="8911e-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="8911e-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8911e-115">E_INVALIDARG</span></span>|<span data-ttu-id="8911e-116">`pAddress` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="8911e-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8911e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8911e-117">Remarks</span></span>  
 <span data-ttu-id="8911e-118">Döndürülen değerin `pAddress` iç çerçeve diğer çerçeveler yığında göreli konumunu belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8911e-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="8911e-119">Hatta IA-64 tabanlı bilgisayarlar iç çerçeve yalnızca yığın üzerinde bulunacağı ve yedekleme deposu için karşılık gelen bir işaretçi yok.</span><span class="sxs-lookup"><span data-stu-id="8911e-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8911e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8911e-120">Requirements</span></span>  
 <span data-ttu-id="8911e-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8911e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8911e-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8911e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8911e-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8911e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8911e-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8911e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8911e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8911e-125">See Also</span></span>  
 [<span data-ttu-id="8911e-126">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8911e-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="8911e-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8911e-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8911e-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8911e-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

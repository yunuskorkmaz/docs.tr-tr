---
title: ICorDebugManagedCallback::ControlCTrap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f4794fb0383435f828626497036ad3458df2173
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204997"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="64e7d-102">ICorDebugManagedCallback::ControlCTrap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64e7d-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="64e7d-103">Hata ayıklayıcı, CTRL + C ayıklanmakta olan işlemin yakalanır bildirir.</span><span class="sxs-lookup"><span data-stu-id="64e7d-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64e7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64e7d-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64e7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64e7d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="64e7d-106">[in] CTRL + C ', yakalanan işlemini temsil eden bir Icordebugprocess nesneye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64e7d-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64e7d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64e7d-107">Return Value</span></span>  
  
|<span data-ttu-id="64e7d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64e7d-108">HRESULT</span></span>|<span data-ttu-id="64e7d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64e7d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64e7d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="64e7d-110">S_OK</span></span>|<span data-ttu-id="64e7d-111">Hata ayıklayıcı, CTRL + C yakalama işleyecektir.</span><span class="sxs-lookup"><span data-stu-id="64e7d-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="64e7d-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="64e7d-112">S_FALSE</span></span>|<span data-ttu-id="64e7d-113">Hata ayıklayıcı CTRL + C yakalama işlememesi.</span><span class="sxs-lookup"><span data-stu-id="64e7d-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64e7d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64e7d-114">Remarks</span></span>  
 <span data-ttu-id="64e7d-115">İşlemdeki tüm uygulama etki alanları için bu geri çağırma durdurulur.</span><span class="sxs-lookup"><span data-stu-id="64e7d-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64e7d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64e7d-116">Requirements</span></span>  
 <span data-ttu-id="64e7d-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64e7d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64e7d-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64e7d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64e7d-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64e7d-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="64e7d-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="64e7d-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64e7d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64e7d-121">See also</span></span>

- [<span data-ttu-id="64e7d-122">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64e7d-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

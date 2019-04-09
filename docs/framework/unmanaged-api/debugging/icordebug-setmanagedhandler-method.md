---
title: ICorDebug::SetManagedHandler Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f30089879f2d023c8fb04b52e75b2942da2a83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130175"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="cdc34-102">ICorDebug::SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdc34-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="cdc34-103">Yönetilen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cdc34-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdc34-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdc34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdc34-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="cdc34-106">[in] Bir işaretçi bir [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) olay işleyici nesnesi olan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="cdc34-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdc34-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdc34-107">Remarks</span></span>  
 `SetManagedHandler` <span data-ttu-id="cdc34-108">oluşturma zamanında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cdc34-108">must be called at creation time.</span></span>  
  
 <span data-ttu-id="cdc34-109">Varsa `ICorDebugManagedCallback` uygulama ayıklanmakta olan, uygulama için hata ayıklama olaylarını işlemek için yeterli arabirimleri içermiyor `SetManagedHandler` , bir HRESULT e_noınterface döndürür.</span><span class="sxs-lookup"><span data-stu-id="cdc34-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdc34-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdc34-110">Requirements</span></span>  
 <span data-ttu-id="cdc34-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdc34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdc34-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdc34-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdc34-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdc34-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cdc34-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="cdc34-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cdc34-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdc34-115">See also</span></span>

- [<span data-ttu-id="cdc34-116">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdc34-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

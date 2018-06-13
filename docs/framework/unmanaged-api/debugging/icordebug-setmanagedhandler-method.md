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
ms.openlocfilehash: bcf97f9fffabb9ae9579016517cfc335e6f783a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404579"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="b922f-102">ICorDebug::SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b922f-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="b922f-103">Yönetilen olayları için olay işleyici nesnesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b922f-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b922f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b922f-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b922f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b922f-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="b922f-106">[in] Bir işaretçi bir [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) olay işleyici nesnesi nesne.</span><span class="sxs-lookup"><span data-stu-id="b922f-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b922f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b922f-107">Remarks</span></span>  
 <span data-ttu-id="b922f-108">`SetManagedHandler` oluşturma sırasında çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b922f-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="b922f-109">Varsa `ICorDebugManagedCallback` uygulaması ayıklanacak, uygulama için hata ayıklama olayları işlemek için yeterli arabirimleri içermiyor `SetManagedHandler` , bir HRESULT E_NOINTERFACE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b922f-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b922f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b922f-110">Requirements</span></span>  
 <span data-ttu-id="b922f-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b922f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b922f-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b922f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b922f-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b922f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b922f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b922f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b922f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b922f-115">See Also</span></span>  
 [<span data-ttu-id="b922f-116">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b922f-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

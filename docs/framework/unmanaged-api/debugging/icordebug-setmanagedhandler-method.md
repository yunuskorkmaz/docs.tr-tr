---
title: "ICorDebug::SetManagedHandler Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetManagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06f0989058ed21e736fde0aee5f1cd1dd66e0ca8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="ff3d7-102">ICorDebug::SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff3d7-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="ff3d7-103">Yönetilen olayları için olay işleyici nesnesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff3d7-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff3d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff3d7-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff3d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff3d7-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="ff3d7-106">[in] Bir işaretçi bir [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) olay işleyici nesnesi nesne.</span><span class="sxs-lookup"><span data-stu-id="ff3d7-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff3d7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff3d7-107">Remarks</span></span>  
 <span data-ttu-id="ff3d7-108">`SetManagedHandler`oluşturma sırasında çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff3d7-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="ff3d7-109">Varsa `ICorDebugManagedCallback` uygulaması ayıklanacak, uygulama için hata ayıklama olayları işlemek için yeterli arabirimleri içermiyor `SetManagedHandler` , bir HRESULT E_NOINTERFACE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff3d7-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff3d7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff3d7-110">Requirements</span></span>  
 <span data-ttu-id="ff3d7-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff3d7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff3d7-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff3d7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff3d7-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff3d7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff3d7-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff3d7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff3d7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff3d7-115">See Also</span></span>  
 [<span data-ttu-id="ff3d7-116">Icordebug arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff3d7-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

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
ms.openlocfilehash: 88a007654646ba42ebcaf1b42e002282a1040c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134058"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="45329-102">ICorDebug::SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45329-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="45329-103">Yönetilen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="45329-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45329-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45329-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45329-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45329-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="45329-106">'ndaki Olay işleyicisi nesnesi olan [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="45329-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45329-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45329-107">Remarks</span></span>  
 <span data-ttu-id="45329-108">`SetManagedHandler` oluşturma zamanında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="45329-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="45329-109">`ICorDebugManagedCallback` uygulaması, hata ayıklamakta olan uygulama için hata ayıklama olaylarını işlemek üzere yeterli arabirimler içermiyorsa, `SetManagedHandler` bir HRESULT E_NOINTERFACE döndürür.</span><span class="sxs-lookup"><span data-stu-id="45329-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45329-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45329-110">Requirements</span></span>  
 <span data-ttu-id="45329-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45329-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45329-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="45329-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45329-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="45329-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45329-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45329-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45329-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45329-115">See also</span></span>

- [<span data-ttu-id="45329-116">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45329-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

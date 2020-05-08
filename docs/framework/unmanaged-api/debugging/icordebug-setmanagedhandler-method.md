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
ms.openlocfilehash: a197d260c55d24f906da7d7f2768bb7ba1ad751f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895341"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="50e27-102">ICorDebug::SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e27-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="50e27-103">Yönetilen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="50e27-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50e27-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50e27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50e27-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="50e27-106">'ndaki Olay işleyicisi nesnesi olan [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="50e27-106">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50e27-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50e27-107">Remarks</span></span>  
 <span data-ttu-id="50e27-108">`SetManagedHandler`Oluşturulma zamanında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50e27-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="50e27-109">`ICorDebugManagedCallback` Uygulama, hataları ayıklanan uygulamanın hata ayıklama olaylarını işlemek için yeterli arabirimler içermiyorsa, `SetManagedHandler` E_NOINTERFACE hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="50e27-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e27-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50e27-110">Requirements</span></span>  
 <span data-ttu-id="50e27-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e27-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e27-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50e27-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50e27-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="50e27-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e27-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e27-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e27-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50e27-115">See also</span></span>

- [<span data-ttu-id="50e27-116">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50e27-116">ICorDebug Interface</span></span>](icordebug-interface.md)

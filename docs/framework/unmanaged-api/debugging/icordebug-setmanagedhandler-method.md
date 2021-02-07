---
description: ': ICorDebug:: SetManagedHandler yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5817bd39a2c4e7c71dc12ca8d2d9b1263d116ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754361"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="ae0b4-103">ICorDebug::SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae0b4-103">ICorDebug::SetManagedHandler Method</span></span>

<span data-ttu-id="ae0b4-104">Yönetilen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae0b4-104">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae0b4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae0b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae0b4-106">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="ae0b4-107">'ndaki Olay işleyicisi nesnesi olan [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae0b4-107">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae0b4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae0b4-108">Remarks</span></span>  

 <span data-ttu-id="ae0b4-109">`SetManagedHandler` Oluşturulma zamanında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae0b4-109">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="ae0b4-110">Uygulama, `ICorDebugManagedCallback` hataları ayıklanan uygulamanın hata ayıklama olaylarını işlemek için yeterli arabirimler içermiyorsa, `SetManagedHandler` E_NOINTERFACE hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae0b4-110">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae0b4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae0b4-111">Requirements</span></span>  

 <span data-ttu-id="ae0b4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae0b4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae0b4-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae0b4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae0b4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae0b4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae0b4-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae0b4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0b4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae0b4-116">See also</span></span>

- [<span data-ttu-id="ae0b4-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae0b4-117">ICorDebug Interface</span></span>](icordebug-interface.md)

---
title: ICorDebug::SetUnmanagedHandler Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1be18d374bad07b590096acac985812c2e2ed9b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407590"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="82a93-102">ICorDebug::SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82a93-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="82a93-103">Yönetilmeyen olayları için olay işleyici nesnesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="82a93-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82a93-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82a93-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82a93-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82a93-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="82a93-106">[in] Bir işaretçi bir [Icordebugunmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) yönetilmeyen olayları için olay işleyicisini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="82a93-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82a93-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82a93-107">Remarks</span></span>  
 <span data-ttu-id="82a93-108">Olay işleyicisi nesne yönetilmeyen için olayları ayarlayın, sonra yapılan bir çağrı [Icordebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) ve yapılan her çağrı önce [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) veya [Icordebug::DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="82a93-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="82a93-109">Ancak, eski amaçları için ilk yerel hata ayıklama olay tetiklenir kadar yönetilmeyen olayları için olay işleyici nesnesi ayarlamak için gerekmez.</span><span class="sxs-lookup"><span data-stu-id="82a93-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="82a93-110">Özellikle, `ICorDebug::CreateProcess` AfxBeginThread'e bayrak, yerel hata ayıklama olayları olamaz gönderilen ana iş parçacığı sürdürülene kadar ayarladı.</span><span class="sxs-lookup"><span data-stu-id="82a93-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82a93-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82a93-111">Requirements</span></span>  
 <span data-ttu-id="82a93-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82a93-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82a93-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82a93-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82a93-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82a93-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82a93-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82a93-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a93-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82a93-116">See Also</span></span>  
 [<span data-ttu-id="82a93-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a93-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

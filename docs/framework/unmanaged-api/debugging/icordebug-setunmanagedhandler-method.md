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
ms.openlocfilehash: c234b3953130f53d7e6b583cd92670149a70689b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168876"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="bb7d8-102">ICorDebug::SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb7d8-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="bb7d8-103">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb7d8-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb7d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb7d8-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb7d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb7d8-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="bb7d8-106">[in] Bir işaretçi bir [Icordebugunmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) yönetilmeyen olayları için olay işleyicisini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="bb7d8-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb7d8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb7d8-107">Remarks</span></span>  
 <span data-ttu-id="bb7d8-108">Olay işleyicisi nesne yönetilmeyen için olayları ayarlayın, sonra bir çağrı [Icordebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) ve çağrıları önce [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) veya [Icordebug::DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="bb7d8-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="bb7d8-109">Ancak, eski amaçları için ilk yerel hata ayıklama olayı kadar yönetilmeyen olayları için olay işleyicisi nesnesi ayarlamak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="bb7d8-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="bb7d8-110">Özellikle, `ICorDebug::CreateProcess` CREATE_SUSPENDED bayrağını, yerel hata ayıklama olaylarını kullanılamaz dağıtılan ana iş parçacığı sürdürülene kadar.</span><span class="sxs-lookup"><span data-stu-id="bb7d8-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb7d8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb7d8-111">Requirements</span></span>  
 <span data-ttu-id="bb7d8-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb7d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb7d8-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb7d8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb7d8-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb7d8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb7d8-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb7d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb7d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb7d8-116">See also</span></span>

- [<span data-ttu-id="bb7d8-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb7d8-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

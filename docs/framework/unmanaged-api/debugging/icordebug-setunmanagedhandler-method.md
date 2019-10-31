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
ms.openlocfilehash: 36d314211d95dff6648753f5d550a2cfd402a918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134042"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="9f38b-102">ICorDebug::SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f38b-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="9f38b-103">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f38b-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f38b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f38b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f38b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f38b-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="9f38b-106">'ndaki Yönetilmeyen olaylar için olay işleyicisini temsil eden [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f38b-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f38b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f38b-107">Remarks</span></span>  
 <span data-ttu-id="9f38b-108">Yönetilmeyen olaylar için olay işleyicisi nesnesi [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) :: Initialize ve ICorDebug: [: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) veya [ICorDebug::D ebugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)çağrılarına yapılan çağrıdan sonra ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f38b-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="9f38b-109">Ancak, eski amaçlar için, ilk yerel hata ayıklama olayı oluşturuluncaya kadar yönetilmeyen olaylar için olay işleyicisi nesnesini ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9f38b-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="9f38b-110">Özellikle, `ICorDebug::CreateProcess` CREATE_SUSPENDED bayrağını ayarlandıysa, ana iş parçacığı sürdürülene kadar yerel hata ayıklama olayları dağıtılamaz.</span><span class="sxs-lookup"><span data-stu-id="9f38b-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f38b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f38b-111">Requirements</span></span>  
 <span data-ttu-id="9f38b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f38b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f38b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9f38b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f38b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9f38b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f38b-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f38b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f38b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f38b-116">See also</span></span>

- [<span data-ttu-id="9f38b-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f38b-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

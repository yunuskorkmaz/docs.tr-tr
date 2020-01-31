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
ms.openlocfilehash: cafa1c99a8988c199d866796911d1983aabb7208
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785061"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="d0eff-102">ICorDebug::SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0eff-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="d0eff-103">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0eff-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0eff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0eff-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0eff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0eff-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="d0eff-106">'ndaki Yönetilmeyen olaylar için olay işleyicisini temsil eden [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0eff-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0eff-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0eff-107">Remarks</span></span>  
 <span data-ttu-id="d0eff-108">Yönetilmeyen olaylar için olay işleyicisi nesnesi [ICorDebug](icordebug-initialize-method.md) :: Initialize ve ICorDebug: [: CreateProcess](icordebug-createprocess-method.md) veya [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md)çağrılarına yapılan çağrıdan sonra ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0eff-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="d0eff-109">Ancak, eski amaçlar için, ilk yerel hata ayıklama olayı oluşturuluncaya kadar yönetilmeyen olaylar için olay işleyicisi nesnesini ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d0eff-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="d0eff-110">Özellikle, `ICorDebug::CreateProcess` CREATE_SUSPENDED bayrağını ayarlandıysa, ana iş parçacığı sürdürülene kadar yerel hata ayıklama olayları dağıtılamaz.</span><span class="sxs-lookup"><span data-stu-id="d0eff-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0eff-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0eff-111">Requirements</span></span>  
 <span data-ttu-id="d0eff-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0eff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0eff-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0eff-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0eff-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d0eff-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0eff-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0eff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0eff-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0eff-116">See also</span></span>

- [<span data-ttu-id="d0eff-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0eff-117">ICorDebug Interface</span></span>](icordebug-interface.md)

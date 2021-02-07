---
description: ': ICorDebug:: SetUnmanagedHandler yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ffd4eb7ff0056a2468ec53eb3534434c2c8d556a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754335"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="6cdd1-103">ICorDebug::SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6cdd1-103">ICorDebug::SetUnmanagedHandler Method</span></span>

<span data-ttu-id="6cdd1-104">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cdd1-104">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cdd1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cdd1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cdd1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6cdd1-106">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="6cdd1-107">'ndaki Yönetilmeyen olaylar için olay işleyicisini temsil eden [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6cdd1-107">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cdd1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cdd1-108">Remarks</span></span>  

 <span data-ttu-id="6cdd1-109">Yönetilmeyen olaylar için olay işleyicisi nesnesi [ICorDebug](icordebug-initialize-method.md) :: Initialize ve ICorDebug: [: CreateProcess](icordebug-createprocess-method.md) veya [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md)çağrılarına yapılan çağrıdan sonra ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6cdd1-109">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="6cdd1-110">Ancak, eski amaçlar için, ilk yerel hata ayıklama olayı oluşturuluncaya kadar yönetilmeyen olaylar için olay işleyicisi nesnesini ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6cdd1-110">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="6cdd1-111">Özellikle `ICorDebug::CreateProcess` CREATE_SUSPENDED bayrağını ayarlandıysa, ana iş parçacığı sürdürülene kadar yerel hata ayıklama olayları dağıtılamaz.</span><span class="sxs-lookup"><span data-stu-id="6cdd1-111">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cdd1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cdd1-112">Requirements</span></span>  

 <span data-ttu-id="6cdd1-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cdd1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cdd1-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6cdd1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cdd1-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6cdd1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cdd1-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cdd1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdd1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cdd1-117">See also</span></span>

- [<span data-ttu-id="6cdd1-118">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cdd1-118">ICorDebug Interface</span></span>](icordebug-interface.md)

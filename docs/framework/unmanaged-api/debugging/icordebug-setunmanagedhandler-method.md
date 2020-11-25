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
ms.openlocfilehash: 0bce14a6853c872d27057b9fffc32b54c59abf13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723395"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="9398b-102">ICorDebug::SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9398b-102">ICorDebug::SetUnmanagedHandler Method</span></span>

<span data-ttu-id="9398b-103">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9398b-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9398b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9398b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9398b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9398b-105">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="9398b-106">'ndaki Yönetilmeyen olaylar için olay işleyicisini temsil eden [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9398b-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9398b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9398b-107">Remarks</span></span>  

 <span data-ttu-id="9398b-108">Yönetilmeyen olaylar için olay işleyicisi nesnesi [ICorDebug](icordebug-initialize-method.md) :: Initialize ve ICorDebug: [: CreateProcess](icordebug-createprocess-method.md) veya [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md)çağrılarına yapılan çağrıdan sonra ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9398b-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="9398b-109">Ancak, eski amaçlar için, ilk yerel hata ayıklama olayı oluşturuluncaya kadar yönetilmeyen olaylar için olay işleyicisi nesnesini ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9398b-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="9398b-110">Özellikle `ICorDebug::CreateProcess` CREATE_SUSPENDED bayrağını ayarlandıysa, ana iş parçacığı sürdürülene kadar yerel hata ayıklama olayları dağıtılamaz.</span><span class="sxs-lookup"><span data-stu-id="9398b-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9398b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9398b-111">Requirements</span></span>  

 <span data-ttu-id="9398b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9398b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9398b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9398b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9398b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9398b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9398b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9398b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9398b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9398b-116">See also</span></span>

- [<span data-ttu-id="9398b-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9398b-117">ICorDebug Interface</span></span>](icordebug-interface.md)

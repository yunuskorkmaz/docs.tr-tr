---
title: ICorDebugController::EnumerateThreads Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: 4d69f13d4716b43c815148ff0fe4aa087b57c6e5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892751"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="af5a1-102">ICorDebugController::EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af5a1-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="af5a1-103">İşlemdeki etkin yönetilen iş parçacıkları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="af5a1-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af5a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af5a1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af5a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af5a1-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="af5a1-106">dışı İşlemde etkin olan tüm yönetilen iş parçacıkları için bir numaralandırıcısı temsil eden "ICorDebugThreadEnum" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="af5a1-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af5a1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af5a1-107">Remarks</span></span>  
 <span data-ttu-id="af5a1-108">[ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) geri çağırması gönderildikten sonra ve [ICorDebugManagedCallback:: ExitThread](icordebugmanagedcallback-exitthread-method.md) geri çağırması gönderildikten sonra bir iş parçacığı etkin kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="af5a1-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="af5a1-109">Yönetilen bir iş parçacığında Stack üzerinde herhangi bir yönetilen çerçeve bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="af5a1-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="af5a1-110">İş parçacıkları [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırmadan önce bile Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="af5a1-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="af5a1-111">Sabit Listesi doğal olarak boş olur.</span><span class="sxs-lookup"><span data-stu-id="af5a1-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af5a1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af5a1-112">Requirements</span></span>  
 <span data-ttu-id="af5a1-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af5a1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af5a1-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af5a1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af5a1-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="af5a1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af5a1-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af5a1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5a1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af5a1-117">See also</span></span>

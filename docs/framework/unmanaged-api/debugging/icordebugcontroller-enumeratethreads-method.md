---
description: ': ICorDebugController:: EnumerateThreads yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b53425de36be5a435ef0dac538c5165f41db63f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710783"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="d3a3e-103">ICorDebugController::EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3a3e-103">ICorDebugController::EnumerateThreads Method</span></span>

<span data-ttu-id="d3a3e-104">İşlemdeki etkin yönetilen iş parçacıkları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d3a3e-104">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a3e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3a3e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3a3e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3a3e-106">Parameters</span></span>  

 `ppThreads`  
 <span data-ttu-id="d3a3e-107">dışı İşlemde etkin olan tüm yönetilen iş parçacıkları için bir numaralandırıcısı temsil eden "ICorDebugThreadEnum" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d3a3e-107">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3a3e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3a3e-108">Remarks</span></span>  

 <span data-ttu-id="d3a3e-109">[ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) geri çağırması gönderildikten sonra ve [ICorDebugManagedCallback:: ExitThread](icordebugmanagedcallback-exitthread-method.md) geri çağırması gönderildikten sonra bir iş parçacığı etkin kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d3a3e-109">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="d3a3e-110">Yönetilen bir iş parçacığında Stack üzerinde herhangi bir yönetilen çerçeve bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d3a3e-110">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="d3a3e-111">İş parçacıkları [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırmadan önce bile Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3a3e-111">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="d3a3e-112">Sabit Listesi doğal olarak boş olur.</span><span class="sxs-lookup"><span data-stu-id="d3a3e-112">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3a3e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3a3e-113">Requirements</span></span>  

 <span data-ttu-id="d3a3e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3a3e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3a3e-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d3a3e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3a3e-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3a3e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3a3e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3a3e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a3e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3a3e-118">See also</span></span>

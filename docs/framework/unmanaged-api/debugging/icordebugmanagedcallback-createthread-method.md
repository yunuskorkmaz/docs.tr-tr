---
description: ': ICorDebugManagedCallback:: CreateThread yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugManagedCallback::CreateThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 20d5ce9da34e7082502252eeece2ab34b1f2e902
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791040"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="cc720-103">ICorDebugManagedCallback::CreateThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc720-103">ICorDebugManagedCallback::CreateThread Method</span></span>

<span data-ttu-id="cc720-104">Hata ayıklayıcıya bir iş parçacığının yönetilen kodu yürütmeye başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="cc720-104">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc720-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc720-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc720-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc720-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="cc720-107">'ndaki İş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc720-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="cc720-108">'ndaki İş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc720-108">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc720-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc720-109">Remarks</span></span>  

 <span data-ttu-id="cc720-110">İş parçacığı yürütülecek ilk yönetilen kod yönergesinde konumlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="cc720-110">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc720-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc720-111">Requirements</span></span>  

 <span data-ttu-id="cc720-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc720-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc720-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc720-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc720-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc720-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc720-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc720-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc720-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc720-116">See also</span></span>

- [<span data-ttu-id="cc720-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc720-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

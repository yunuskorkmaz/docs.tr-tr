---
title: "ICorDebugManagedCallback::CreateThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 525ad78142d624e840cb71330556fda952b1d2d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="21286-102">ICorDebugManagedCallback::CreateThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21286-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="21286-103">Hata ayıklayıcı bir iş parçacığı yönetilen kod yürütmeyi başlattı bildirir.</span><span class="sxs-lookup"><span data-stu-id="21286-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21286-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21286-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21286-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21286-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="21286-106">[in] İş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21286-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="21286-107">[in] Bir işaretçi Icordebugthread nesneye iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21286-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21286-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21286-108">Remarks</span></span>  
 <span data-ttu-id="21286-109">İş parçacığı yürütülecek ilk yönetilen kod yönerge yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="21286-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21286-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21286-110">Requirements</span></span>  
 <span data-ttu-id="21286-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21286-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21286-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21286-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21286-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21286-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21286-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21286-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21286-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21286-115">See Also</span></span>  
 [<span data-ttu-id="21286-116">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="21286-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

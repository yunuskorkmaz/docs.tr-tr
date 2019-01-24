---
title: ICorDebugManagedCallback::ExitThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8abe1b63aad7b73b3260553550112ded75b77bb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537744"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="55200-102">ICorDebugManagedCallback::ExitThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55200-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="55200-103">Hata ayıklayıcı, yönetilen kod yürütülmekte olan bir iş parçacığı çıkıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="55200-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55200-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55200-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55200-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55200-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="55200-106">[in] Yönetilen iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="55200-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="55200-107">[in] Yönetilen iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="55200-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55200-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55200-108">Remarks</span></span>  
 <span data-ttu-id="55200-109">Bir kez `ExitThread` geri çağırma tetiklenir, iş parçacığının iş parçacığı numaralandırmalardan görünmeyecek.</span><span class="sxs-lookup"><span data-stu-id="55200-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55200-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55200-110">Requirements</span></span>  
 <span data-ttu-id="55200-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55200-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55200-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55200-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55200-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55200-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55200-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55200-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55200-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55200-115">See also</span></span>
- [<span data-ttu-id="55200-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55200-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

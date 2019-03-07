---
title: ICorDebugManagedCallback::Exception Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e985d82fcce404e15344f2277d27a6aab45f9efc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472514"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="99ff6-102">ICorDebugManagedCallback::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99ff6-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="99ff6-103">Hata ayıklayıcı, yönetilen koddan bir özel durum olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="99ff6-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ff6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99ff6-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99ff6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99ff6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="99ff6-106">[in] Özel durumun oluştuğu uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="99ff6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="99ff6-107">[in] Özel durumun oluştuğu iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="99ff6-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="99ff6-108">[in] Bu değer ise `false`, özel durum henüz henüz olup Aksi takdirde uygulama tarafından işlenen özel durum işlenmemiş ve işlemini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="99ff6-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99ff6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99ff6-109">Remarks</span></span>  
 <span data-ttu-id="99ff6-110">Özel durum iş parçacığı nesnesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="99ff6-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99ff6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99ff6-111">Requirements</span></span>  
 <span data-ttu-id="99ff6-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99ff6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99ff6-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99ff6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99ff6-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99ff6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99ff6-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99ff6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ff6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99ff6-116">See also</span></span>
- [<span data-ttu-id="99ff6-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99ff6-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

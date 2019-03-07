---
title: ICorDebugManagedCallback2::ExceptionUnwind Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 802d4987b3be86b5a6302b78f75e4f0c02d49f3e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492042"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="891ea-102">ICorDebugManagedCallback2::ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="891ea-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="891ea-103">Özel durumu geriye doğru işlem sırasında bir durum bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="891ea-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="891ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="891ea-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="891ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="891ea-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="891ea-106">[in] Özel durumun oluştuğu iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="891ea-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="891ea-107">[in] Özel durumun oluştuğu iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="891ea-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="891ea-108">[in] Geri çağırma tarafından geriye doğru izleme aşamasında sinyal olayı belirtir CorDebugExceptionUnwindCallbackType sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="891ea-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="891ea-109">[in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ek bilgi belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="891ea-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="891ea-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="891ea-110">Remarks</span></span>  
 <span data-ttu-id="891ea-111">`ExceptionUnwind` çeşitli noktalarda, özel durum işleme işleminin geriye doğru izleme aşamasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="891ea-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="891ea-112">`ExceptionUnwind` birden çok kez tek bir özel durumu geriye doğru izleme çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="891ea-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="891ea-113">Varsa `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, yönerge işaretçisini dizisi noktadan önce iş parçacığının yaprak çerçevesinde olacaktır (önce birkaç yönergeleri olabilir) özel duruma yol açan yönerge.</span><span class="sxs-lookup"><span data-stu-id="891ea-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="891ea-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="891ea-114">Requirements</span></span>  
 <span data-ttu-id="891ea-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="891ea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="891ea-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="891ea-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="891ea-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="891ea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="891ea-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="891ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="891ea-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="891ea-119">See also</span></span>
- [<span data-ttu-id="891ea-120">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="891ea-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="891ea-121">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="891ea-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

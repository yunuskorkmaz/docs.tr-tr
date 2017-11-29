---
title: "ICorDebugManagedCallback2::ExceptionUnwind Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45b9f5838e4bc98e3f269a2cebd575abfe998a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="04e08-102">ICorDebugManagedCallback2::ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e08-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="04e08-103">Özel durum unwinding işlemi sırasında bir durum bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="04e08-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04e08-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04e08-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04e08-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="04e08-106">[in] Bir işaretçi Icordebugappdomain nesneye özel durum oluştu iş parçacığı içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="04e08-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="04e08-107">[in] Bir işaretçi Icordebugthread nesneye özel durum oluştu iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="04e08-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="04e08-108">[in] Geri çağırma göre geriye doğru izleme aşamasında işaret olayı belirtir CorDebugExceptionUnwindCallbackType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="04e08-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="04e08-109">[in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ayrıntılı bilgileri belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="04e08-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04e08-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04e08-110">Remarks</span></span>  
 <span data-ttu-id="04e08-111">`ExceptionUnwind`çeşitli noktalarda, özel durum işleme işleminin bırakma aşamasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="04e08-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="04e08-112">`ExceptionUnwind`birden çok kez tek bir özel durum geriye doğru izleme sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="04e08-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="04e08-113">Varsa `dwEventType` DEBUG_EXCEPTION_INTERCEPTED, = yönerge işaretçisi önce dizisi noktada iş parçacığının yaprak çerçevesinde olacaktır (önce birkaç yönergeleri olabilir) özel durumu öncülük yönerge.</span><span class="sxs-lookup"><span data-stu-id="04e08-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e08-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04e08-114">Requirements</span></span>  
 <span data-ttu-id="04e08-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e08-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e08-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04e08-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04e08-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04e08-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04e08-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e08-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e08-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04e08-119">See Also</span></span>  
 [<span data-ttu-id="04e08-120">Icordebugmanagedcallback2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e08-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="04e08-121">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e08-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

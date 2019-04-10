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
ms.openlocfilehash: faba9631e85ac84ff1517b64e9a3f5567ee7c9dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214801"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="8f974-102">ICorDebugManagedCallback2::ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f974-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="8f974-103">Özel durumu geriye doğru işlem sırasında bir durum bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f974-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f974-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f974-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f974-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f974-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8f974-106">[in] Özel durumun oluştuğu iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8f974-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8f974-107">[in] Özel durumun oluştuğu iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8f974-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="8f974-108">[in] Geri çağırma tarafından geriye doğru izleme aşamasında sinyal olayı belirtir CorDebugExceptionUnwindCallbackType sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="8f974-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8f974-109">[in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ek bilgi belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="8f974-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f974-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f974-110">Remarks</span></span>  
 `ExceptionUnwind` <span data-ttu-id="8f974-111">çeşitli noktalarda, özel durum işleme işleminin geriye doğru izleme aşamasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8f974-111">is called at various points during the unwind phase of the exception-handling process.</span></span> `ExceptionUnwind` <span data-ttu-id="8f974-112">birden çok kez tek bir özel durumu geriye doğru izleme çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f974-112">can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="8f974-113">Varsa `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, yönerge işaretçisini dizisi noktadan önce iş parçacığının yaprak çerçevesinde olacaktır (önce birkaç yönergeleri olabilir) özel duruma yol açan yönerge.</span><span class="sxs-lookup"><span data-stu-id="8f974-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f974-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f974-114">Requirements</span></span>  
 <span data-ttu-id="8f974-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f974-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f974-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f974-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f974-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f974-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8f974-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="8f974-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f974-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f974-119">See also</span></span>

- [<span data-ttu-id="8f974-120">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f974-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="8f974-121">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f974-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

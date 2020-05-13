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
ms.openlocfilehash: 8f66369d3ac5ddcfe38fe579cac728eb3a250165
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205620"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="431d9-102">ICorDebugManagedCallback2::ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="431d9-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="431d9-103">Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="431d9-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="431d9-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="431d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="431d9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="431d9-106">'ndaki Özel durumun oluşturulduğu iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="431d9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="431d9-107">'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="431d9-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="431d9-108">'ndaki Geriye doğru izleme aşamasında geri çağırma tarafından bildirimekte olan olayı belirten Cordebugexceptionunwınizcallbacktype numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="431d9-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="431d9-109">'ndaki Özel durum hakkında ek bilgi belirten [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="431d9-109">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="431d9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="431d9-110">Remarks</span></span>  
 <span data-ttu-id="431d9-111">`ExceptionUnwind`, özel durum işleme sürecinin geriye doğru izleme aşamasında çeşitli noktalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="431d9-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="431d9-112">`ExceptionUnwind`tek bir özel durum geriye doğru bir şekilde bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="431d9-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="431d9-113">Eğer `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, yönerge işaretçisi, iş parçacığının yaprak çerçevesinde (daha önce birkaç yönerge olabilir) özel duruma yol gösteren yönerge olur.</span><span class="sxs-lookup"><span data-stu-id="431d9-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="431d9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="431d9-114">Requirements</span></span>  
 <span data-ttu-id="431d9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="431d9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="431d9-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="431d9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="431d9-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="431d9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="431d9-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="431d9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431d9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="431d9-119">See also</span></span>

- [<span data-ttu-id="431d9-120">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="431d9-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="431d9-121">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="431d9-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

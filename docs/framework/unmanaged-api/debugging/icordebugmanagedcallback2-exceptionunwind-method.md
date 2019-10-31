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
ms.openlocfilehash: fa317e1217ac0a9ca46bfeb312446534b1fca63a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131559"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="ff0d2-102">ICorDebugManagedCallback2::ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff0d2-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="ff0d2-103">Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff0d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff0d2-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff0d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff0d2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ff0d2-106">'ndaki Özel durumun oluşturulduğu iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ff0d2-107">'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="ff0d2-108">'ndaki Geriye doğru izleme aşamasında geri çağırma tarafından bildirimekte olan olayı belirten Cordebugexceptionunwınizcallbacktype numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ff0d2-109">'ndaki Özel durum hakkında ek bilgi belirten [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff0d2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff0d2-110">Remarks</span></span>  
 <span data-ttu-id="ff0d2-111">`ExceptionUnwind`, özel durum işleme sürecinin geriye doğru izleme aşamasında çeşitli noktalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="ff0d2-112">tek bir özel durum geriye doğru bir şekilde `ExceptionUnwind` birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="ff0d2-113">`dwEventType` = DEBUG_EXCEPTION_INTERCEPTED ise yönerge işaretçisi, özel duruma yol gösteren yönerge olan iş parçacığının yaprak çerçevesinde (daha önce birkaç yönerge olabilir) olur.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff0d2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff0d2-114">Requirements</span></span>  
 <span data-ttu-id="ff0d2-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff0d2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff0d2-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff0d2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff0d2-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ff0d2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff0d2-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff0d2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0d2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff0d2-119">See also</span></span>

- [<span data-ttu-id="ff0d2-120">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff0d2-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="ff0d2-121">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff0d2-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

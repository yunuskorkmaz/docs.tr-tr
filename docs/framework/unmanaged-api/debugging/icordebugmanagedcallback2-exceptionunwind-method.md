---
description: 'Daha fazla bilgi edinin: ICorDebugManagedCallback2:: Exceptionaçılım yöntemi'
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
ms.openlocfilehash: 2d98fb21cdbb0db25a11761ac9b00e99e1526cc0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790857"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="2cbd1-103">ICorDebugManagedCallback2::ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2cbd1-103">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>

<span data-ttu-id="2cbd1-104">Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-104">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbd1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cbd1-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cbd1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2cbd1-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="2cbd1-107">'ndaki Özel durumun oluşturulduğu iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2cbd1-108">'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-108">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="2cbd1-109">'ndaki Geriye doğru izleme aşamasında geri çağırma tarafından bildirimekte olan olayı belirten Cordebugexceptionunwınizcallbacktype numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-109">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2cbd1-110">'ndaki Özel durum hakkında ek bilgi belirten [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-110">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cbd1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cbd1-111">Remarks</span></span>  

 <span data-ttu-id="2cbd1-112">`ExceptionUnwind` , özel durum işleme sürecinin geriye doğru izleme aşamasında çeşitli noktalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-112">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="2cbd1-113">`ExceptionUnwind` tek bir özel durum geriye doğru bir şekilde bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-113">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="2cbd1-114">Eğer `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, yönerge işaretçisi, iş parçacığının yaprak çerçevesinde (daha önce birkaç yönerge olabilir) özel duruma yol gösteren yönerge olur.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-114">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cbd1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cbd1-115">Requirements</span></span>  

 <span data-ttu-id="2cbd1-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cbd1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cbd1-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2cbd1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cbd1-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2cbd1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cbd1-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cbd1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbd1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-120">See also</span></span>

- [<span data-ttu-id="2cbd1-121">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cbd1-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="2cbd1-122">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cbd1-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

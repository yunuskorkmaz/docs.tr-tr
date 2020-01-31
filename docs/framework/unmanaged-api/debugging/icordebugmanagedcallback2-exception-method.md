---
title: ICorDebugManagedCallback2::Exception Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: e7125d923fb1d3757bb4ca53f5a7db806b241dd9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781528"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="ef49d-102">ICorDebugManagedCallback2::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef49d-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="ef49d-103">Hata ayıklayıcıya bir özel durum işleyici aramasının başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="ef49d-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef49d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef49d-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef49d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef49d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ef49d-106">'ndaki Özel durumun oluşturulduğu iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ef49d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ef49d-107">'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ef49d-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="ef49d-108">'ndaki `dwEventType` parametresi tarafından belirlendiği şekilde, bir çerçeveyi temsil eden ICorDebugFrame nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ef49d-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="ef49d-109">Daha fazla bilgi için, açıklamalar bölümündeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="ef49d-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="ef49d-110">'ndaki `dwEventType` parametresi tarafından belirlendiği şekilde, bir sapmayı belirten tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ef49d-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="ef49d-111">Daha fazla bilgi için, açıklamalar bölümündeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="ef49d-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="ef49d-112">'ndaki Bu özel durum geri çağrısının türünü belirten CorDebugExceptionCallbackType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="ef49d-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ef49d-113">'ndaki Özel durum hakkında ek bilgi belirten [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) sabit listesinin bir değeri</span><span class="sxs-lookup"><span data-stu-id="ef49d-113">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef49d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef49d-114">Remarks</span></span>  
 <span data-ttu-id="ef49d-115">`Exception` geri çağırması, özel durum işleme işleminin arama aşamasında çeşitli noktalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ef49d-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="ef49d-116">Diğer bir deyişle, özel durum geriye doğru bir şekilde bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef49d-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="ef49d-117">İşlenmekte olan özel durum, `pThread` parametresi tarafından başvurulan ICorDebugThread nesnesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="ef49d-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="ef49d-118">Belirli bir çerçeve ve fark, `dwEventType` parametresine göre belirlenir:</span><span class="sxs-lookup"><span data-stu-id="ef49d-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="ef49d-119">`dwEventType` değeri</span><span class="sxs-lookup"><span data-stu-id="ef49d-119">Value of `dwEventType`</span></span>|<span data-ttu-id="ef49d-120">`pFrame` değeri</span><span class="sxs-lookup"><span data-stu-id="ef49d-120">Value of `pFrame`</span></span>|<span data-ttu-id="ef49d-121">`nOffset` değeri</span><span class="sxs-lookup"><span data-stu-id="ef49d-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="ef49d-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ef49d-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="ef49d-123">Özel durumu oluşturan çerçeve.</span><span class="sxs-lookup"><span data-stu-id="ef49d-123">The frame that threw the exception.</span></span>|<span data-ttu-id="ef49d-124">Çerçevedeki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ef49d-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="ef49d-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ef49d-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="ef49d-126">Oluşturulan özel durum noktasına en yakın Kullanıcı kodu çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="ef49d-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="ef49d-127">Çerçevedeki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ef49d-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="ef49d-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="ef49d-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="ef49d-129">Catch işleyicisini içeren çerçeve.</span><span class="sxs-lookup"><span data-stu-id="ef49d-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="ef49d-130">Catch işleyicisinin başlangıcının Microsoft ara dili (MSIL) kayması.</span><span class="sxs-lookup"><span data-stu-id="ef49d-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="ef49d-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="ef49d-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="ef49d-132">NULL</span><span class="sxs-lookup"><span data-stu-id="ef49d-132">NULL</span></span>|<span data-ttu-id="ef49d-133">Tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="ef49d-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef49d-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef49d-134">Requirements</span></span>  
 <span data-ttu-id="ef49d-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef49d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef49d-136">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef49d-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef49d-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ef49d-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef49d-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef49d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef49d-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef49d-139">See also</span></span>

- [<span data-ttu-id="ef49d-140">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef49d-140">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="ef49d-141">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef49d-141">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

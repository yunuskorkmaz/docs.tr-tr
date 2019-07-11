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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd707685dfff31644565db18e72dc153d25781f4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761083"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="dc613-102">ICorDebugManagedCallback2::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc613-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="dc613-103">Hata ayıklayıcı özel durum işleyicisi için arama başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="dc613-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc613-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc613-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dc613-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc613-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dc613-106">[in] Özel durumun oluştuğu iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dc613-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="dc613-107">[in] Özel durumun oluştuğu iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dc613-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="dc613-108">[in] Bir çerçeve tarafından belirlenen şekilde temsil eden bir Icordebugframe nesne işaretçisi `dwEventType` parametresi.</span><span class="sxs-lookup"><span data-stu-id="dc613-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="dc613-109">Daha fazla bilgi için Açıklamalar bölümü içindeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="dc613-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="dc613-110">[in] Tarafından belirlenen şekilde bir uzaklık belirten bir tamsayı `dwEventType` parametresi.</span><span class="sxs-lookup"><span data-stu-id="dc613-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="dc613-111">Daha fazla bilgi için Açıklamalar bölümü içindeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="dc613-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="dc613-112">[in] Bu özel durum geri arama türünü belirten CorDebugExceptionCallbackType sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="dc613-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dc613-113">[in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ek bilgi belirten sabit listesi</span><span class="sxs-lookup"><span data-stu-id="dc613-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc613-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc613-114">Remarks</span></span>  
 <span data-ttu-id="dc613-115">`Exception` Geri çağırma çeşitli noktalarda özel durum işleme işleminin arama aşamasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="dc613-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="dc613-116">Diğer bir deyişle, çağrılabilir birden çok kez bir özel durumu geriye doğru izleme çalışırken.</span><span class="sxs-lookup"><span data-stu-id="dc613-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="dc613-117">İşlenmekte olan özel durum tarafından başvurulan Icordebugthread nesnesinden alınabilir `pThread` parametresi.</span><span class="sxs-lookup"><span data-stu-id="dc613-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="dc613-118">Uzaklık ve belirli çerçeve tarafından belirlenen `dwEventType` parametresini aşağıdaki şekilde:</span><span class="sxs-lookup"><span data-stu-id="dc613-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="dc613-119">Değeri `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="dc613-119">Value of `dwEventType`</span></span>|<span data-ttu-id="dc613-120">Değeri `pFrame`</span><span class="sxs-lookup"><span data-stu-id="dc613-120">Value of `pFrame`</span></span>|<span data-ttu-id="dc613-121">Değeri `nOffset`</span><span class="sxs-lookup"><span data-stu-id="dc613-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="dc613-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="dc613-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="dc613-123">Özel durum oluşturdu çerçeve.</span><span class="sxs-lookup"><span data-stu-id="dc613-123">The frame that threw the exception.</span></span>|<span data-ttu-id="dc613-124">Çerçevede yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dc613-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="dc613-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="dc613-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="dc613-126">Oluşturulan özel durumun noktaya en yakın kullanıcı kodu çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="dc613-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="dc613-127">Çerçevede yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dc613-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="dc613-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="dc613-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="dc613-129">Catch işleyicisi içeren çerçeve.</span><span class="sxs-lookup"><span data-stu-id="dc613-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="dc613-130">Catch işleyicisi başına Microsoft Ara dili (MSIL) uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="dc613-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="dc613-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="dc613-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="dc613-132">NULL</span><span class="sxs-lookup"><span data-stu-id="dc613-132">NULL</span></span>|<span data-ttu-id="dc613-133">Tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="dc613-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc613-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc613-134">Requirements</span></span>  
 <span data-ttu-id="dc613-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc613-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc613-136">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc613-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc613-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc613-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc613-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc613-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc613-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc613-139">See also</span></span>

- [<span data-ttu-id="dc613-140">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc613-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="dc613-141">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc613-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

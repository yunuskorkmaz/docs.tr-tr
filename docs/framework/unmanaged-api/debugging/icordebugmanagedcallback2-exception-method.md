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
ms.openlocfilehash: f8952b34781045089945e7e72e179e88300b5fdd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103356"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="0dafb-102">ICorDebugManagedCallback2::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dafb-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="0dafb-103">Hata ayıklayıcı özel durum işleyicisi için arama başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="0dafb-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dafb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dafb-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dafb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0dafb-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0dafb-106">[in] Özel durumun oluştuğu iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0dafb-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="0dafb-107">[in] Özel durumun oluştuğu iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0dafb-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="0dafb-108">[in] Bir çerçeve tarafından belirlenen şekilde temsil eden bir Icordebugframe nesne işaretçisi `dwEventType` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0dafb-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="0dafb-109">Daha fazla bilgi için Açıklamalar bölümü içindeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="0dafb-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="0dafb-110">[in] Tarafından belirlenen şekilde bir uzaklık belirten bir tamsayı `dwEventType` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0dafb-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="0dafb-111">Daha fazla bilgi için Açıklamalar bölümü içindeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="0dafb-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="0dafb-112">[in] Bu özel durum geri arama türünü belirten CorDebugExceptionCallbackType sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="0dafb-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0dafb-113">[in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ek bilgi belirten sabit listesi</span><span class="sxs-lookup"><span data-stu-id="0dafb-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dafb-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dafb-114">Remarks</span></span>  
 <span data-ttu-id="0dafb-115">`Exception` Geri çağırma çeşitli noktalarda özel durum işleme işleminin arama aşamasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0dafb-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="0dafb-116">Diğer bir deyişle, çağrılabilir birden çok kez bir özel durumu geriye doğru izleme çalışırken.</span><span class="sxs-lookup"><span data-stu-id="0dafb-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="0dafb-117">İşlenmekte olan özel durum tarafından başvurulan Icordebugthread nesnesinden alınabilir `pThread` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0dafb-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="0dafb-118">Uzaklık ve belirli çerçeve tarafından belirlenen `dwEventType` parametresini aşağıdaki şekilde:</span><span class="sxs-lookup"><span data-stu-id="0dafb-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="0dafb-119">Değeri</span><span class="sxs-lookup"><span data-stu-id="0dafb-119">Value of</span></span> `dwEventType`|<span data-ttu-id="0dafb-120">Değeri</span><span class="sxs-lookup"><span data-stu-id="0dafb-120">Value of</span></span> `pFrame`|<span data-ttu-id="0dafb-121">Değeri</span><span class="sxs-lookup"><span data-stu-id="0dafb-121">Value of</span></span> `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="0dafb-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0dafb-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="0dafb-123">Özel durum oluşturdu çerçeve.</span><span class="sxs-lookup"><span data-stu-id="0dafb-123">The frame that threw the exception.</span></span>|<span data-ttu-id="0dafb-124">Çerçevede yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0dafb-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="0dafb-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0dafb-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="0dafb-126">Oluşturulan özel durumun noktaya en yakın kullanıcı kodu çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="0dafb-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="0dafb-127">Çerçevede yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0dafb-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="0dafb-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="0dafb-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="0dafb-129">Catch işleyicisi içeren çerçeve.</span><span class="sxs-lookup"><span data-stu-id="0dafb-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="0dafb-130">Catch işleyicisi başına Microsoft Ara dili (MSIL) uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="0dafb-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="0dafb-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="0dafb-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="0dafb-132">NULL</span><span class="sxs-lookup"><span data-stu-id="0dafb-132">NULL</span></span>|<span data-ttu-id="0dafb-133">Tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="0dafb-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0dafb-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dafb-134">Requirements</span></span>  
 <span data-ttu-id="0dafb-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dafb-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dafb-136">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0dafb-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dafb-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dafb-137">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0dafb-138">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0dafb-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0dafb-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dafb-139">See also</span></span>

- [<span data-ttu-id="0dafb-140">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dafb-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="0dafb-141">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dafb-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

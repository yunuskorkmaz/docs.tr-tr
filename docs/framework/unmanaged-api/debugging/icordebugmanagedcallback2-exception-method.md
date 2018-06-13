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
ms.openlocfilehash: faefff879142d66c4c596f1b30a25e349a4014b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421807"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="7eb2d-102">ICorDebugManagedCallback2::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7eb2d-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="7eb2d-103">Hata ayıklayıcı bir özel durum işleyici için bir arama başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb2d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7eb2d-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="7eb2d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7eb2d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7eb2d-106">[in] Bir işaretçi Icordebugappdomain nesneye özel durum oluştu iş parçacığı içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="7eb2d-107">[in] Bir işaretçi Icordebugthread nesneye özel durum oluştu iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="7eb2d-108">[in] Tarafından belirlenen şekilde bir çerçeve temsil eden bir Icordebugframe nesnesi için bir işaretçi `dwEventType` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="7eb2d-109">Daha fazla bilgi için açıklamalar bölümündeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="7eb2d-110">[in] Tarafından belirlenen şekilde bir uzaklık belirten bir tamsayı `dwEventType` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="7eb2d-111">Daha fazla bilgi için açıklamalar bölümündeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="7eb2d-112">[in] Bu özel durum geri çağırma türünü belirtir CorDebugExceptionCallbackType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7eb2d-113">[in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ayrıntılı bilgileri belirtir numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7eb2d-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eb2d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7eb2d-114">Remarks</span></span>  
 <span data-ttu-id="7eb2d-115">`Exception` Geri çağırma çeşitli noktalarda, özel durum işleme işleminin arama aşamasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="7eb2d-116">Diğer bir deyişle, onu çağrılabilir birden çok kez bir özel durum geriye doğru izleme açıkken.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="7eb2d-117">İşlenmekte olan özel durum tarafından başvurulan Icordebugthread nesnesinden alınabilir `pThread` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="7eb2d-118">Uzaklık ve belirli çerçevesi tarafından belirlenen `dwEventType` şekilde parametre:</span><span class="sxs-lookup"><span data-stu-id="7eb2d-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="7eb2d-119">Değeri `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="7eb2d-119">Value of `dwEventType`</span></span>|<span data-ttu-id="7eb2d-120">Değeri `pFrame`</span><span class="sxs-lookup"><span data-stu-id="7eb2d-120">Value of `pFrame`</span></span>|<span data-ttu-id="7eb2d-121">Değeri `nOffset`</span><span class="sxs-lookup"><span data-stu-id="7eb2d-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="7eb2d-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7eb2d-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="7eb2d-123">Özel durum oluşturdu çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-123">The frame that threw the exception.</span></span>|<span data-ttu-id="7eb2d-124">Yönerge işaretçisi çerçevesinde.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="7eb2d-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7eb2d-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="7eb2d-126">Kullanıcı kodu çerçeve oluşturulan özel durum noktasına yakın.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="7eb2d-127">Yönerge işaretçisi çerçevesinde.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="7eb2d-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="7eb2d-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="7eb2d-129">Catch işleyicisini içeren çerçeve.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="7eb2d-130">Catch işleyicisi başlangıcını Microsoft Ara dili (MSIL) uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="7eb2d-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="7eb2d-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="7eb2d-132">NULL</span><span class="sxs-lookup"><span data-stu-id="7eb2d-132">NULL</span></span>|<span data-ttu-id="7eb2d-133">Tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7eb2d-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7eb2d-134">Requirements</span></span>  
 <span data-ttu-id="7eb2d-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb2d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb2d-136">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7eb2d-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7eb2d-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eb2d-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eb2d-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb2d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb2d-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7eb2d-139">See Also</span></span>  
 [<span data-ttu-id="7eb2d-140">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7eb2d-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="7eb2d-141">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7eb2d-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

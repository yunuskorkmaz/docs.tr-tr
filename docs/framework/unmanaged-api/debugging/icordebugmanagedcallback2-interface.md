---
title: ICorDebugManagedCallback2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2
helpviewer_keywords: ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d5b8ac63d200e54d25b58870089f6c062397186
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="50073-102">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50073-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="50073-103">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="50073-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="50073-104">`ICorDebugManagedCallback2`mantıksal bir uzantısıdır ve [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="50073-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50073-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50073-105">Methods</span></span>  
  
|<span data-ttu-id="50073-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="50073-106">Method</span></span>|<span data-ttu-id="50073-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50073-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50073-108">ChangeConnection yöntemi</span><span class="sxs-lookup"><span data-stu-id="50073-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="50073-109">Hata ayıklayıcı belirtilen bağlantı ile ilişkili görevlerin değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="50073-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="50073-110">CreateConnection yöntemi</span><span class="sxs-lookup"><span data-stu-id="50073-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="50073-111">Hata ayıklayıcı yeni bir bağlantı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="50073-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="50073-112">DestroyConnection yöntemi</span><span class="sxs-lookup"><span data-stu-id="50073-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="50073-113">Hata ayıklayıcı belirtilen bağlantı sonlandırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="50073-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="50073-114">Exception yöntemi</span><span class="sxs-lookup"><span data-stu-id="50073-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="50073-115">Hata ayıklayıcı bir özel durum işleyici için bir arama başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="50073-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="50073-116">ExceptionUnwind yöntemi</span><span class="sxs-lookup"><span data-stu-id="50073-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="50073-117">Özel durum unwinding işlemi sırasında bir durum bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="50073-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="50073-118">FunctionRemapComplete yöntemi</span><span class="sxs-lookup"><span data-stu-id="50073-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="50073-119">Hata ayıklayıcı kod yürütmeyi düzenlenen işlevi yeni bir sürüme geçirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="50073-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="50073-120">FunctionRemapOpportunity yöntemi</span><span class="sxs-lookup"><span data-stu-id="50073-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="50073-121">Hata ayıklayıcı kod yürütmeyi bir dizi noktası düzenlenen işlevi daha eski bir sürümünde ulaştı bildirir.</span><span class="sxs-lookup"><span data-stu-id="50073-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="50073-122">MDANotification yöntemi</span><span class="sxs-lookup"><span data-stu-id="50073-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="50073-123">Kod yürütmeyi yönetilen hata ayıklama Yardımcısı (MDA) ileti karşılaştı bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="50073-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50073-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50073-124">Remarks</span></span>  
 <span data-ttu-id="50073-125">`ICorDebugManagedCallback2` Arabirimi genişletiyor `ICorDebugManagedCallback` .NET Framework 2.0 sürümünde sunulan yeni hata ayıklama olayları işlemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="50073-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="50073-126">Bir hata ayıklayıcısı uygulamalıdır `ICorDebugManagedCallback2` .NET Framework 2.0 uygulamaları hata ayıklama durumunda.</span><span class="sxs-lookup"><span data-stu-id="50073-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="50073-127">Örneği `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` geri çağırma nesnesi olarak geçirilen [Icordebug::setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="50073-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50073-128">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="50073-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50073-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50073-129">Requirements</span></span>  
 <span data-ttu-id="50073-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50073-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50073-131">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50073-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50073-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50073-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50073-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50073-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50073-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50073-134">See Also</span></span>  
 [<span data-ttu-id="50073-135">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="50073-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="50073-136">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50073-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="50073-137">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="50073-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

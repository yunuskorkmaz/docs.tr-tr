---
title: ICorDebugManagedCallback2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c9b81536bd39c6879161526cc96c136b71b3172
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548004"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="1c550-102">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c550-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="1c550-103">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c550-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="1c550-104">`ICorDebugManagedCallback2` öğesinin mantıksal uzantısıdır [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1c550-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c550-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1c550-105">Methods</span></span>  
  
|<span data-ttu-id="1c550-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1c550-106">Method</span></span>|<span data-ttu-id="1c550-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c550-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c550-108">ChangeConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c550-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="1c550-109">Hata ayıklayıcı, belirtilen bağlantı ile ilişkili görevlerin değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c550-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="1c550-110">CreateConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c550-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="1c550-111">Hata ayıklayıcı, yeni bir bağlantı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c550-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="1c550-112">DestroyConnection Metodu</span><span class="sxs-lookup"><span data-stu-id="1c550-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="1c550-113">Hata ayıklayıcı, belirtilen bağlantı sonlandırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c550-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="1c550-114">Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c550-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="1c550-115">Hata ayıklayıcı özel durum işleyicisi için arama başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c550-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="1c550-116">ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c550-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="1c550-117">Özel durumu geriye doğru işlem sırasında bir durum bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c550-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="1c550-118">FunctionRemapComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c550-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="1c550-119">Hata ayıklayıcı, yürütmeyi düzenlenmiş bir işlevin yeni bir sürüme geçti bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c550-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="1c550-120">FunctionRemapOpportunity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c550-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="1c550-121">Hata ayıklayıcı, yürütmeyi bir dizi noktası düzenlenmiş bir işlevin daha eski bir sürümünde ulaştı bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c550-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="1c550-122">MDANotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c550-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="1c550-123">Kod yürütmeyi bir yönetilen hata ayıklama Yardımcısı (MDA) iletisini karşılaştı bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c550-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c550-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c550-124">Remarks</span></span>  
 <span data-ttu-id="1c550-125">`ICorDebugManagedCallback2` Arabirimini genişletir `ICorDebugManagedCallback` .NET Framework 2.0 sürümünde tanıtılan yeni hata ayıklama olaylarını işlemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="1c550-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="1c550-126">Bir hata ayıklayıcı uygulamalıdır `ICorDebugManagedCallback2` .NET Framework 2.0 uygulamaları hata ayıklaması.</span><span class="sxs-lookup"><span data-stu-id="1c550-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="1c550-127">Örneği `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` için geri çağırma nesnesi olarak geçirilen [Icordebug::setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="1c550-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c550-128">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1c550-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c550-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c550-129">Requirements</span></span>  
 <span data-ttu-id="1c550-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c550-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c550-131">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c550-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c550-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c550-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c550-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c550-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c550-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c550-134">See also</span></span>
- [<span data-ttu-id="1c550-135">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="1c550-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1c550-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1c550-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1c550-137">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c550-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

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
ms.openlocfilehash: 97f103844c38ebd3dbff058bfe96ab953cdba960
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131466"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="2b2a2-102">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="2b2a2-103">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="2b2a2-104">`ICorDebugManagedCallback2`, [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) arabiriminin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b2a2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2b2a2-105">Methods</span></span>  
  
|<span data-ttu-id="2b2a2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2b2a2-106">Method</span></span>|<span data-ttu-id="2b2a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b2a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b2a2-108">ChangeConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="2b2a2-109">Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="2b2a2-110">CreateConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="2b2a2-111">Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="2b2a2-112">DestroyConnection Metodu</span><span class="sxs-lookup"><span data-stu-id="2b2a2-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="2b2a2-113">Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="2b2a2-114">Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="2b2a2-115">Hata ayıklayıcıya bir özel durum işleyici aramasının başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="2b2a2-116">ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="2b2a2-117">Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="2b2a2-118">FunctionRemapComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="2b2a2-119">Kod yürütmenin düzenlenmiş bir işlevin yeni bir sürümüne geçirildiği hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="2b2a2-120">FunctionRemapOpportunity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="2b2a2-121">Kod yürütmenin, düzenlenmiş bir işlevin daha eski bir sürümündeki bir sıra noktasına ulaştığı hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="2b2a2-122">MDANotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="2b2a2-123">Kod yürütmenin yönetilen hata ayıklama Yardımcısı (MDA) iletisiyle karşılaştığından bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b2a2-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b2a2-124">Remarks</span></span>  
 <span data-ttu-id="2b2a2-125">`ICorDebugManagedCallback2` arabirimi .NET Framework 2,0 sürümünde tanıtılan yeni hata ayıklama olaylarını işlemek için `ICorDebugManagedCallback` arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="2b2a2-126">Hata ayıklayıcı .NET Framework 2,0 uygulamalarında hata ayıklaması durumunda `ICorDebugManagedCallback2` uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="2b2a2-127">Bir `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` örneği [ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b2a2-128">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b2a2-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b2a2-129">Requirements</span></span>  
 <span data-ttu-id="2b2a2-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b2a2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b2a2-131">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2b2a2-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b2a2-132">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2b2a2-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b2a2-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b2a2-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2a2-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b2a2-134">See also</span></span>

- [<span data-ttu-id="2b2a2-135">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="2b2a2-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2b2a2-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2b2a2-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2b2a2-137">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b2a2-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

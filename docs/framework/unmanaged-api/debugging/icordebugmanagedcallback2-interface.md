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
ms.openlocfilehash: ca33436d98edf5844a5ca27c9ac89648f10ec0c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909977"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="dba6b-102">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dba6b-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="dba6b-103">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dba6b-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="dba6b-104">`ICorDebugManagedCallback2`, [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) arabiriminin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="dba6b-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dba6b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dba6b-105">Methods</span></span>  
  
|<span data-ttu-id="dba6b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dba6b-106">Method</span></span>|<span data-ttu-id="dba6b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dba6b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dba6b-108">ChangeConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dba6b-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="dba6b-109">Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="dba6b-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="dba6b-110">CreateConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dba6b-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="dba6b-111">Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="dba6b-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="dba6b-112">DestroyConnection Metodu</span><span class="sxs-lookup"><span data-stu-id="dba6b-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="dba6b-113">Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="dba6b-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="dba6b-114">Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dba6b-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="dba6b-115">Hata ayıklayıcıya bir özel durum işleyici aramasının başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="dba6b-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="dba6b-116">ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dba6b-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="dba6b-117">Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dba6b-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="dba6b-118">FunctionRemapComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dba6b-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="dba6b-119">Kod yürütmenin düzenlenmiş bir işlevin yeni bir sürümüne geçirildiği hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="dba6b-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="dba6b-120">FunctionRemapOpportunity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dba6b-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="dba6b-121">Kod yürütmenin, düzenlenmiş bir işlevin daha eski bir sürümündeki bir sıra noktasına ulaştığı hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="dba6b-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="dba6b-122">MDANotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dba6b-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="dba6b-123">Kod yürütmenin yönetilen hata ayıklama Yardımcısı (MDA) iletisiyle karşılaştığından bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="dba6b-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dba6b-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dba6b-124">Remarks</span></span>  
 <span data-ttu-id="dba6b-125">Arabirim, .NET Framework sürüm `ICorDebugManagedCallback` 2,0 ' de tanıtılan yeni hata ayıklama olaylarını işlemek için arabirimi genişletir. `ICorDebugManagedCallback2`</span><span class="sxs-lookup"><span data-stu-id="dba6b-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="dba6b-126">Hata ayıklayıcı .NET Framework 2,0 `ICorDebugManagedCallback2` uygulamalarında hata ayıklaması durumunda uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dba6b-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="dba6b-127">`ICorDebugManagedCallback` Veya`ICorDebugManagedCallback2` örneği [ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="dba6b-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dba6b-128">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="dba6b-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba6b-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dba6b-129">Requirements</span></span>  
 <span data-ttu-id="dba6b-130">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba6b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba6b-131">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dba6b-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dba6b-132">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dba6b-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba6b-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba6b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba6b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dba6b-134">See also</span></span>

- [<span data-ttu-id="dba6b-135">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="dba6b-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="dba6b-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dba6b-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="dba6b-137">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dba6b-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

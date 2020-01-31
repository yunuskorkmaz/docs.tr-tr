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
ms.openlocfilehash: 43982ebb634843c0130c3321aa84c90b84e8c786
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793310"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="394ce-102">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="394ce-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="394ce-103">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="394ce-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="394ce-104">`ICorDebugManagedCallback2`, [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) arabiriminin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="394ce-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="394ce-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="394ce-105">Methods</span></span>  
  
|<span data-ttu-id="394ce-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="394ce-106">Method</span></span>|<span data-ttu-id="394ce-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="394ce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="394ce-108">ChangeConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394ce-108">ChangeConnection Method</span></span>](icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="394ce-109">Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="394ce-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="394ce-110">CreateConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394ce-110">CreateConnection Method</span></span>](icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="394ce-111">Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="394ce-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="394ce-112">DestroyConnection Metodu</span><span class="sxs-lookup"><span data-stu-id="394ce-112">DestroyConnection Method</span></span>](icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="394ce-113">Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="394ce-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="394ce-114">Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394ce-114">Exception Method</span></span>](icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="394ce-115">Hata ayıklayıcıya bir özel durum işleyici aramasının başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="394ce-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="394ce-116">ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394ce-116">ExceptionUnwind Method</span></span>](icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="394ce-117">Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="394ce-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="394ce-118">FunctionRemapComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394ce-118">FunctionRemapComplete Method</span></span>](icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="394ce-119">Kod yürütmenin düzenlenmiş bir işlevin yeni bir sürümüne geçirildiği hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="394ce-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="394ce-120">FunctionRemapOpportunity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394ce-120">FunctionRemapOpportunity Method</span></span>](icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="394ce-121">Kod yürütmenin, düzenlenmiş bir işlevin daha eski bir sürümündeki bir sıra noktasına ulaştığı hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="394ce-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="394ce-122">MDANotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394ce-122">MDANotification Method</span></span>](icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="394ce-123">Kod yürütmenin yönetilen hata ayıklama Yardımcısı (MDA) iletisiyle karşılaştığından bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="394ce-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="394ce-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="394ce-124">Remarks</span></span>  
 <span data-ttu-id="394ce-125">`ICorDebugManagedCallback2` arabirimi .NET Framework 2,0 sürümünde tanıtılan yeni hata ayıklama olaylarını işlemek için `ICorDebugManagedCallback` arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="394ce-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="394ce-126">Hata ayıklayıcı .NET Framework 2,0 uygulamalarında hata ayıklaması durumunda `ICorDebugManagedCallback2` uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="394ce-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="394ce-127">Bir `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` örneği [ICorDebug:: SetManagedHandler](icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="394ce-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="394ce-128">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="394ce-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="394ce-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="394ce-129">Requirements</span></span>  
 <span data-ttu-id="394ce-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="394ce-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="394ce-131">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="394ce-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="394ce-132">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="394ce-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="394ce-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="394ce-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394ce-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="394ce-134">See also</span></span>

- [<span data-ttu-id="394ce-135">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="394ce-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="394ce-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="394ce-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="394ce-137">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="394ce-137">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

---
description: 'Daha fazla bilgi edinin: ICorDebugManagedCallback2 Interface'
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
ms.openlocfilehash: a6a5b05479ea0f9e2d86f7c0ce42f5edd35bcb7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691763"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="cea15-103">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cea15-103">ICorDebugManagedCallback2 Interface</span></span>

<span data-ttu-id="cea15-104">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cea15-104">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="cea15-105">`ICorDebugManagedCallback2` , [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) arabiriminin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="cea15-105">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cea15-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cea15-106">Methods</span></span>  
  
|<span data-ttu-id="cea15-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cea15-107">Method</span></span>|<span data-ttu-id="cea15-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cea15-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cea15-109">ChangeConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cea15-109">ChangeConnection Method</span></span>](icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="cea15-110">Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="cea15-110">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="cea15-111">CreateConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cea15-111">CreateConnection Method</span></span>](icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="cea15-112">Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="cea15-112">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="cea15-113">DestroyConnection Metodu</span><span class="sxs-lookup"><span data-stu-id="cea15-113">DestroyConnection Method</span></span>](icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="cea15-114">Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="cea15-114">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="cea15-115">Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cea15-115">Exception Method</span></span>](icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="cea15-116">Hata ayıklayıcıya bir özel durum işleyici aramasının başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="cea15-116">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="cea15-117">ExceptionUnwind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cea15-117">ExceptionUnwind Method</span></span>](icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="cea15-118">Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cea15-118">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="cea15-119">FunctionRemapComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cea15-119">FunctionRemapComplete Method</span></span>](icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="cea15-120">Kod yürütmenin düzenlenmiş bir işlevin yeni bir sürümüne geçirildiği hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="cea15-120">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="cea15-121">FunctionRemapOpportunity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cea15-121">FunctionRemapOpportunity Method</span></span>](icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="cea15-122">Kod yürütmenin, düzenlenmiş bir işlevin daha eski bir sürümündeki bir sıra noktasına ulaştığı hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="cea15-122">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="cea15-123">MDANotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cea15-123">MDANotification Method</span></span>](icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="cea15-124">Kod yürütmenin yönetilen hata ayıklama Yardımcısı (MDA) iletisiyle karşılaştığından bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="cea15-124">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cea15-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cea15-125">Remarks</span></span>  

 <span data-ttu-id="cea15-126">`ICorDebugManagedCallback2`Arabirim, `ICorDebugManagedCallback` .NET Framework sürüm 2,0 ' de tanıtılan yeni hata ayıklama olaylarını işlemek için arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="cea15-126">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="cea15-127">Hata ayıklayıcı `ICorDebugManagedCallback2` .NET Framework 2,0 uygulamalarında hata ayıklaması durumunda uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cea15-127">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="cea15-128">`ICorDebugManagedCallback`Veya örneği `ICorDebugManagedCallback2` [ICorDebug:: SetManagedHandler](icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cea15-128">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cea15-129">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="cea15-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cea15-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cea15-130">Requirements</span></span>  

 <span data-ttu-id="cea15-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cea15-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cea15-132">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cea15-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cea15-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cea15-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cea15-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cea15-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea15-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cea15-135">See also</span></span>

- [<span data-ttu-id="cea15-136">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="cea15-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cea15-137">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cea15-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cea15-138">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cea15-138">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

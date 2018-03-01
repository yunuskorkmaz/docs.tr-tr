---
title: "ICorDebugManagedCallback::LogSwitch Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: beb4dc25d634f64d8740005abf83e51ec1e3e731
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="137b6-102">ICorDebugManagedCallback::LogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="137b6-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="137b6-103">Hata ayıklayıcı ortak dil çalışma zamanı (CLR) yönetilen iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.Switch> sınıfı oluşturmak, değiştirmek veya bir hata ayıklama izleme anahtarı silin.</span><span class="sxs-lookup"><span data-stu-id="137b6-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="137b6-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="137b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="137b6-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="137b6-106">[in] Bir işaretçi Icordebugappdomain nesneye oluşturulan, değiştirilen veya bir hata ayıklama izlemeyi anahtar silinen yönetilen iş parçacığı içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="137b6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="137b6-107">[in] Yönetilen iş parçacığı temsil eden bir Icordebugthread nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="137b6-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="137b6-108">[in] Olay günlüğüne yazılan açıklayıcı ileti önem derecesi belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="137b6-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="137b6-109">[in] Değerini [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) işlemi belirten numaralandırma gerçekleştirilen hata ayıklama izleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="137b6-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="137b6-110">[in] Hata ayıklama izlemeyi anahtarın adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="137b6-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="137b6-111">[in] Hata ayıklama izleme anahtarı üst adını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="137b6-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="137b6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="137b6-112">Requirements</span></span>  
 <span data-ttu-id="137b6-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="137b6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="137b6-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="137b6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="137b6-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="137b6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="137b6-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="137b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137b6-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="137b6-117">See Also</span></span>  
 [<span data-ttu-id="137b6-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="137b6-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

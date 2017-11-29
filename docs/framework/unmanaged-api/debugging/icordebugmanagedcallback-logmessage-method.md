---
title: "ICorDebugManagedCallback::LogMessage Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LogMessage
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f06e737498f2c12b041467f5f66de55c602615f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="700a8-102">ICorDebugManagedCallback::LogMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="700a8-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="700a8-103">Hata ayıklayıcı ortak dil çalışma zamanı (CLR) yönetilen iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.EventLog> sınıfı bir olayı günlüğe kaydedin.</span><span class="sxs-lookup"><span data-stu-id="700a8-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="700a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="700a8-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="700a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="700a8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="700a8-106">[in] Bir işaretçi Icordebugappdomain nesneye olayı günlüğe kaydeden yönetilen iş parçacığı içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="700a8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="700a8-107">[in] Yönetilen iş parçacığı temsil eden bir Icordebugthread nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="700a8-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="700a8-108">[in] Değerini [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) olay günlüğüne yazılan açıklayıcı ileti önem derecesi gösterir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="700a8-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="700a8-109">[in] İzleme anahtarı adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="700a8-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="700a8-110">[in] Olay günlüğüne yazılan iletisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="700a8-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="700a8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="700a8-111">Requirements</span></span>  
 <span data-ttu-id="700a8-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="700a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="700a8-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="700a8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="700a8-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="700a8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="700a8-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="700a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700a8-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="700a8-116">See Also</span></span>  
 [<span data-ttu-id="700a8-117">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="700a8-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

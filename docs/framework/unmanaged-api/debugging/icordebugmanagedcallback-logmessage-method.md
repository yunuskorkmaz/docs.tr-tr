---
title: ICorDebugManagedCallback::LogMessage Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf83124af5ced7bb6458564430ceb319ce7d680a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099163"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="d889b-102">ICorDebugManagedCallback::LogMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d889b-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="d889b-103">Hata ayıklayıcı ortak dil çalışma zamanı (CLR) yönetilen iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.EventLog> günlüğe bir olay için sınıf.</span><span class="sxs-lookup"><span data-stu-id="d889b-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d889b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d889b-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d889b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d889b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d889b-106">[in] Olayın günlüğe yönetilen iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d889b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d889b-107">[in] Yönetilen iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d889b-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="d889b-108">[in] Değerini [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) olay günlüğüne yazılmış açıklayıcı bir ileti önem derecesi belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d889b-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="d889b-109">[in] İzleme anahtarı adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d889b-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="d889b-110">[in] Olay günlüğüne yazılmış iletisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d889b-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d889b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d889b-111">Requirements</span></span>  
 <span data-ttu-id="d889b-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d889b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d889b-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d889b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d889b-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d889b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d889b-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d889b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d889b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d889b-116">See also</span></span>

- [<span data-ttu-id="d889b-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d889b-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

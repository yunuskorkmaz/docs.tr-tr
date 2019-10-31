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
ms.openlocfilehash: d95662167dbc8fcda049fb6a7b3e6ff1dfb6e736
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130699"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="551fd-102">ICorDebugManagedCallback::LogMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="551fd-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="551fd-103">Hata ayıklayıcısını, ortak dil çalışma zamanı (CLR) yönetilen iş parçacığının, bir olayı günlüğe kaydetmek için <xref:System.Diagnostics.EventLog> sınıfında bir yöntemi çağırdığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="551fd-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="551fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="551fd-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="551fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="551fd-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="551fd-106">'ndaki Olayı günlüğe tutan yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="551fd-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="551fd-107">'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="551fd-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="551fd-108">'ndaki Olay günlüğüne yazılan açıklayıcı iletinin önem derecesini gösteren [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="551fd-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="551fd-109">'ndaki İzleme anahtarı adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="551fd-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="551fd-110">'ndaki Olay günlüğüne yazılan iletiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="551fd-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="551fd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="551fd-111">Requirements</span></span>  
 <span data-ttu-id="551fd-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="551fd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="551fd-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="551fd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="551fd-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="551fd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="551fd-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="551fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551fd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="551fd-116">See also</span></span>

- [<span data-ttu-id="551fd-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="551fd-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

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
ms.openlocfilehash: 4306c4ae44b0ae1ade2bf374981492fa1a4df76f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788377"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="cf0d8-102">ICorDebugManagedCallback::LogMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf0d8-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="cf0d8-103">Hata ayıklayıcısını, ortak dil çalışma zamanı (CLR) yönetilen iş parçacığının, bir olayı günlüğe kaydetmek için <xref:System.Diagnostics.EventLog> sınıfında bir yöntemi çağırdığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="cf0d8-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf0d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf0d8-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf0d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf0d8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cf0d8-106">'ndaki Olayı günlüğe tutan yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf0d8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="cf0d8-107">'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf0d8-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="cf0d8-108">'ndaki Olay günlüğüne yazılan açıklayıcı iletinin önem derecesini gösteren [LoggingLevelEnum](logginglevelenum-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="cf0d8-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="cf0d8-109">'ndaki İzleme anahtarı adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf0d8-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="cf0d8-110">'ndaki Olay günlüğüne yazılan iletiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf0d8-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf0d8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf0d8-111">Requirements</span></span>  
 <span data-ttu-id="cf0d8-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf0d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf0d8-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf0d8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf0d8-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cf0d8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf0d8-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf0d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf0d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf0d8-116">See also</span></span>

- [<span data-ttu-id="cf0d8-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf0d8-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

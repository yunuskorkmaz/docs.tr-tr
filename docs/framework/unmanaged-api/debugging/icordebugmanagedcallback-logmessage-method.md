---
description: ': ICorDebugManagedCallback:: LogMessage yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 199f1f5dca7889a62ef351b4a2731fdb360768d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660524"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="f1c27-103">ICorDebugManagedCallback::LogMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1c27-103">ICorDebugManagedCallback::LogMessage Method</span></span>

<span data-ttu-id="f1c27-104">Hata ayıklayıcıyı bir ortak dil çalışma zamanı (CLR) yönetilen iş parçacığının, <xref:System.Diagnostics.EventLog> bir olayı günlüğe kaydetmek için sınıfında bir yöntemi çağırdığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="f1c27-104">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1c27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1c27-105">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1c27-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1c27-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="f1c27-107">'ndaki Olayı günlüğe tutan yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1c27-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f1c27-108">'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1c27-108">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="f1c27-109">'ndaki Olay günlüğüne yazılan açıklayıcı iletinin önem derecesini gösteren [LoggingLevelEnum](logginglevelenum-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="f1c27-109">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="f1c27-110">'ndaki İzleme anahtarı adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1c27-110">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="f1c27-111">'ndaki Olay günlüğüne yazılan iletiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1c27-111">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1c27-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1c27-112">Requirements</span></span>  

 <span data-ttu-id="f1c27-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1c27-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1c27-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f1c27-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1c27-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f1c27-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1c27-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1c27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c27-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c27-117">See also</span></span>

- [<span data-ttu-id="f1c27-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1c27-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

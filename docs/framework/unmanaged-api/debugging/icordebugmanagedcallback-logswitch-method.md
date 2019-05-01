---
title: ICorDebugManagedCallback::LogSwitch Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a011485453999b9d764716356eebb2a5462f7bb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988149"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="00c43-102">ICorDebugManagedCallback::LogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00c43-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="00c43-103">Hata ayıklayıcı ortak dil çalışma zamanı (CLR) yönetilen iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.Switch> sınıfı oluşturmak, değiştirmek veya bir hata ayıklama izleme anahtarı silin.</span><span class="sxs-lookup"><span data-stu-id="00c43-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00c43-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00c43-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00c43-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00c43-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="00c43-106">[in] Oluşturulan, değiştirilen veya hata ayıklama izleme anahtarı silindi yönetilen iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="00c43-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="00c43-107">[in] Yönetilen iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="00c43-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="00c43-108">[in] Olay günlüğüne yazılmış açıklayıcı bir ileti önem derecesi belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="00c43-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="00c43-109">[in] Değerini [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) işlemi belirten numaralandırma hata ayıklama izleme anahtarı gerçekleşen.</span><span class="sxs-lookup"><span data-stu-id="00c43-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="00c43-110">[in] Hata ayıklama izleme anahtarı adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="00c43-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="00c43-111">[in] Üst öğesinin hata ayıklama izleme anahtarı adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="00c43-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00c43-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00c43-112">Requirements</span></span>  
 <span data-ttu-id="00c43-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00c43-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00c43-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00c43-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00c43-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00c43-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00c43-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00c43-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c43-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00c43-117">See also</span></span>

- [<span data-ttu-id="00c43-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00c43-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

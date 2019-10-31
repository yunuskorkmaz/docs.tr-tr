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
ms.openlocfilehash: a72eabb1b405c67f5603164e56a589a237603d2f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130688"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="7fe6b-102">ICorDebugManagedCallback::LogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7fe6b-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="7fe6b-103">Hata ayıklayıcıyı bir ortak dil çalışma zamanı (CLR) yönetilen iş parçacığının bir hata ayıklama/izleme anahtarı oluşturmak, değiştirmek veya silmek için <xref:System.Diagnostics.Switch> sınıfında bir yöntemi çağırdığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe6b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7fe6b-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fe6b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7fe6b-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="7fe6b-106">'ndaki Bir hata ayıklama/izleme anahtarını oluşturan, değiştiren veya silen yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="7fe6b-107">'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="7fe6b-108">'ndaki Olay günlüğüne yazılan açıklayıcı iletinin önem derecesini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="7fe6b-109">'ndaki Hata ayıklama/izleme anahtarında gerçekleştirilen işlemi belirten [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="7fe6b-110">'ndaki Hata ayıklama/izleme anahtarının adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="7fe6b-111">'ndaki Hata ayıklama/izleme anahtarının üst öğesinin adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fe6b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7fe6b-112">Requirements</span></span>  
 <span data-ttu-id="7fe6b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fe6b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fe6b-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7fe6b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fe6b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7fe6b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fe6b-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fe6b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe6b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-117">See also</span></span>

- [<span data-ttu-id="7fe6b-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7fe6b-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

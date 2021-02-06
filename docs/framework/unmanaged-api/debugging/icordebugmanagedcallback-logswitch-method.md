---
description: ': ICorDebugManagedCallback:: LogSwitch yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 658b2afbe7074062910670c6748dc579973715f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660472"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="d4e87-103">ICorDebugManagedCallback::LogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4e87-103">ICorDebugManagedCallback::LogSwitch Method</span></span>

<span data-ttu-id="d4e87-104">Hata ayıklayıcıyı bir ortak dil çalışma zamanı (CLR) yönetilen iş parçacığının, <xref:System.Diagnostics.Switch> bir hata ayıklama/izleme anahtarı oluşturmak, değiştirmek veya silmek için sınıfında bir yöntemi çağırdığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="d4e87-104">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e87-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4e87-105">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4e87-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4e87-106">Parameters</span></span>  

 `PAppDomain`  
 <span data-ttu-id="d4e87-107">'ndaki Bir hata ayıklama/izleme anahtarını oluşturan, değiştiren veya silen yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4e87-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d4e87-108">'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4e87-108">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="d4e87-109">'ndaki Olay günlüğüne yazılan açıklayıcı iletinin önem derecesini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="d4e87-109">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="d4e87-110">'ndaki Hata ayıklama/izleme anahtarında gerçekleştirilen işlemi belirten [LogSwitchCallReason](logswitchcallreason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="d4e87-110">[in] A value of the [LogSwitchCallReason](logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="d4e87-111">'ndaki Hata ayıklama/izleme anahtarının adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4e87-111">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="d4e87-112">'ndaki Hata ayıklama/izleme anahtarının üst öğesinin adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4e87-112">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e87-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4e87-113">Requirements</span></span>  

 <span data-ttu-id="d4e87-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4e87-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4e87-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d4e87-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4e87-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d4e87-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4e87-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e87-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e87-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4e87-118">See also</span></span>

- [<span data-ttu-id="d4e87-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e87-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

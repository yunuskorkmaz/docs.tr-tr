---
description: 'Hakkında daha fazla bilgi edinin: LoggingLevelEnum numaralandırması'
title: LoggingLevelEnum Numaralandırması
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 7c9676fef83ea44f45a25350a2b3d325c1c22f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800623"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="71099-103">LoggingLevelEnum Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="71099-103">LoggingLevelEnum Enumeration</span></span>

<span data-ttu-id="71099-104">Yönetilen bir iş parçacığı bir olay günlüğe kaydederken olay günlüğüne yazılan açıklayıcı bir iletinin önem derecesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="71099-104">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71099-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="71099-105">Syntax</span></span>  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="71099-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="71099-106">Members</span></span>  
  
|<span data-ttu-id="71099-107">Üye</span><span class="sxs-lookup"><span data-stu-id="71099-107">Member</span></span>|<span data-ttu-id="71099-108">Description</span><span class="sxs-lookup"><span data-stu-id="71099-108">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="71099-109">İleti bir izleme düzeyi 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="71099-109">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="71099-110">İleti bir izleme düzeyi 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71099-110">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="71099-111">İleti bir izleme düzeyi 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71099-111">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="71099-112">İleti bir izleme düzeyi 3 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71099-112">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="71099-113">İleti bir izleme düzeyi 4 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71099-113">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="71099-114">İleti bir durum düzeyi 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="71099-114">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="71099-115">İleti bir durum düzeyi 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71099-115">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="71099-116">İleti bir durum düzeyi 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71099-116">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="71099-117">İleti bir durum düzeyi 3 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71099-117">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="71099-118">İleti bir durum düzeyi 4 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71099-118">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="71099-119">İleti bir uyarı düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="71099-119">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="71099-120">İleti bir hata düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="71099-120">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="71099-121">İleti bir panik düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="71099-121">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71099-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71099-122">Remarks</span></span>  

 <span data-ttu-id="71099-123">Ortak dil çalışma zamanı (CLR), hata ayıklayıcıya yönetilen bir iş parçacığının günlüğe kaydettiği bir olay olduğunu bildirmek için [ICorDebugManagedCallback:: LogMessage](icordebugmanagedcallback-logmessage-method.md) yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="71099-123">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="71099-124">CLR, `LoggingLevelEnum` yönetilen iş parçacığının olay günlüğüne yazdığı iletinin önem derecesini belirtmek için sabit listesinin bir değerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="71099-124">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71099-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71099-125">Requirements</span></span>  

 <span data-ttu-id="71099-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71099-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71099-127">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="71099-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71099-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="71099-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71099-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71099-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71099-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71099-130">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="71099-131">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="71099-131">Debugging Enumerations</span></span>](debugging-enumerations.md)

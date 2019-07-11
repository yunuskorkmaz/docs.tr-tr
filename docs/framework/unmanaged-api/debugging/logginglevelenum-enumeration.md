---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9659dd835bb60adf8471f73ed45b6588cf15126f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752590"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="6dc0e-102">LoggingLevelEnum Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6dc0e-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="6dc0e-103">Yönetilen iş parçacığı bir olayı günlüğe kaydettiğinde, olay günlüğüne yazılan açıklayıcı bir iletisi önem derecesi düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dc0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6dc0e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6dc0e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6dc0e-105">Members</span></span>  
  
|<span data-ttu-id="6dc0e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6dc0e-106">Member</span></span>|<span data-ttu-id="6dc0e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6dc0e-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="6dc0e-108">İleti izleme düzeyi 0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="6dc0e-109">İleti izleme düzeyini 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="6dc0e-110">İleti izleme düzeyini 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="6dc0e-111">İleti izleme düzeyini 3 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="6dc0e-112">İzleme düzeyi 4 iletisidir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="6dc0e-113">İleti durumu düzeyi 0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="6dc0e-114">İleti durumu düzeyi 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="6dc0e-115">İleti durumu düzeyi 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="6dc0e-116">İleti durumu düzeyi 3 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="6dc0e-117">İleti durumu düzeyi 4 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="6dc0e-118">İleti bir uyarı düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="6dc0e-119">İleti bir hata düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="6dc0e-120">İleti Panik düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dc0e-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6dc0e-121">Remarks</span></span>  
 <span data-ttu-id="6dc0e-122">Ortak dil çalışma zamanı (CLR) çağıran [Icordebugmanagedcallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) yönetilen iş parçacığı günlüğe bir olay, hata ayıklayıcı bildirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="6dc0e-123">CLR değerini geçirir `LoggingLevelEnum` yönetilen iş parçacığı olay günlüğüne yazdığı ileti önem düzeyini belirtmek için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dc0e-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6dc0e-124">Requirements</span></span>  
 <span data-ttu-id="6dc0e-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dc0e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dc0e-126">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6dc0e-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6dc0e-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dc0e-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dc0e-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dc0e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc0e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dc0e-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="6dc0e-130">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6dc0e-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

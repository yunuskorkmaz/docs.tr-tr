---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENTPIPE_LEVEL numaralandırması'
title: COR_PRF_EVENTPIPE_LEVEL numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_LEVEL
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: da8211da1a9bb6262b078c5e56bee1d0c1f9342e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805824"
---
# <a name="cor_prf_eventpipe_level-enumeration"></a><span data-ttu-id="702a7-103">COR_PRF_EVENTPIPE_LEVEL numaralandırması</span><span class="sxs-lookup"><span data-stu-id="702a7-103">COR_PRF_EVENTPIPE_LEVEL Enumeration</span></span>

<span data-ttu-id="702a7-104">Bir EventPipe olayının düzeyini açıklar.</span><span class="sxs-lookup"><span data-stu-id="702a7-104">Describes the level of an EventPipe event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="702a7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="702a7-105">Syntax</span></span>  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_LOGALWAYS = 0,
    COR_PRF_EVENTPIPE_CRITICAL = 1,
    COR_PRF_EVENTPIPE_ERROR = 2,
    COR_PRF_EVENTPIPE_WARNING = 3,
    COR_PRF_EVENTPIPE_INFORMATIONAL = 4,
    COR_PRF_EVENTPIPE_VERBOSE = 5
} COR_PRF_EVENTPIPE_LEVEL;
```  
  
## <a name="members"></a><span data-ttu-id="702a7-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="702a7-106">Members</span></span>  
  
|<span data-ttu-id="702a7-107">Üye</span><span class="sxs-lookup"><span data-stu-id="702a7-107">Member</span></span>|<span data-ttu-id="702a7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="702a7-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_LOGALWAYS`|<span data-ttu-id="702a7-109">Olay her zaman günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="702a7-109">The event is always logged.</span></span>|
|`COR_PRF_EVENTPIPE_CRITICAL`|<span data-ttu-id="702a7-110">Olay, kritik bir iletiyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="702a7-110">The event represents a critical message.</span></span>|
|`COR_PRF_EVENTPIPE_ERROR`|<span data-ttu-id="702a7-111">Olay bir hata iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="702a7-111">The event represents an error message.</span></span>|
|`COR_PRF_EVENTPIPE_WARNING`|<span data-ttu-id="702a7-112">Olay bir uyarı iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="702a7-112">The event represents a warning message.</span></span>|
|`COR_PRF_EVENTPIPE_INFORMATIONAL`|<span data-ttu-id="702a7-113">Olay bir bilgi iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="702a7-113">The event represents an informational message.</span></span>|
|`COR_PRF_EVENTPIPE_VERBOSE`|<span data-ttu-id="702a7-114">Olay, ayrıntılı bir iletiyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="702a7-114">The event represents a verbose message.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="702a7-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="702a7-115">Remarks</span></span>  

 <span data-ttu-id="702a7-116">`COR_PRF_EVENTPIPE_LEVEL`Numaralandırma, tanımlanmakta olan olayın düzeyini göstermek Için [ICorProfilerInfo12:: EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="702a7-116">The `COR_PRF_EVENTPIPE_LEVEL` enumeration is used by the [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) method to indicate the level of the event being defined.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="702a7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="702a7-117">Requirements</span></span>  

<span data-ttu-id="702a7-118">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="702a7-118">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="702a7-119">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="702a7-119">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="702a7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="702a7-120">See also</span></span>

- [<span data-ttu-id="702a7-121">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="702a7-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="702a7-122">ICorProfilerInfo12:: EventPipeDefineEvent</span><span class="sxs-lookup"><span data-stu-id="702a7-122">ICorProfilerInfo12::EventPipeDefineEvent</span></span>](icorprofilerinfo12-eventpipedefineevent-method.md)

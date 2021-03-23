---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENT_DATA numaralandırması'
title: COR_PRF_EVENT_DATA numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENT_DATA
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 477f36476deb9c0d74e263703e36b134c91b5327
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805577"
---
# <a name="cor_prf_event_data-enumeration"></a><span data-ttu-id="640ab-103">COR_PRF_EVENT_DATA numaralandırması</span><span class="sxs-lookup"><span data-stu-id="640ab-103">COR_PRF_EVENT_DATA Enumeration</span></span>

<span data-ttu-id="640ab-104">Yazılan bir EventPipe olayının olay verilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="640ab-104">Describes the event data for an EventPipe event being written.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="640ab-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="640ab-105">Syntax</span></span>  
  
```cpp  
typedef struct
{
    UINT64 ptr;
    UINT32 size;
    UINT32 reserved;
} COR_PRF_EVENT_DATA;
```  
  
## <a name="members"></a><span data-ttu-id="640ab-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="640ab-106">Members</span></span>  
  
|<span data-ttu-id="640ab-107">Üye</span><span class="sxs-lookup"><span data-stu-id="640ab-107">Member</span></span>|<span data-ttu-id="640ab-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="640ab-108">Description</span></span>|  
|------------|-----------------|  
|`ptr`|<span data-ttu-id="640ab-109">Verilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="640ab-109">A pointer to the data.</span></span>|  
|`size`|<span data-ttu-id="640ab-110">Tarafından işaret edilen verilerin boyutu `ptr` .</span><span class="sxs-lookup"><span data-stu-id="640ab-110">The size of the data pointed to by `ptr`.</span></span>|  
|`reserved`|<span data-ttu-id="640ab-111">Ayrılmış uygulamaya özel alan.</span><span class="sxs-lookup"><span data-stu-id="640ab-111">An reserved implementation specific field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="640ab-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="640ab-112">Remarks</span></span>  

 <span data-ttu-id="640ab-113">`COR_PRF_EVENT_DATA`Yapı, yazılan olayın veri yükünü providate Için [ICorProfilerInfo12:: EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="640ab-113">The `COR_PRF_EVENT_DATA` structure is used by the [ICorProfilerInfo12::EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md) method to providate the data payload for the event being written.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="640ab-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="640ab-114">Requirements</span></span>  

<span data-ttu-id="640ab-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="640ab-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="640ab-116">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="640ab-116">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="640ab-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="640ab-117">See also</span></span>

- [<span data-ttu-id="640ab-118">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="640ab-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="640ab-119">ICorProfilerInfo12:: EventPipeWriteEvent</span><span class="sxs-lookup"><span data-stu-id="640ab-119">ICorProfilerInfo12::EventPipeWriteEvent</span></span>](icorprofilerinfo12-eventpipewriteevent-method.md)

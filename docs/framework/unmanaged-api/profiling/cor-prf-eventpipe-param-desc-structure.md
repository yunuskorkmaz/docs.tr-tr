---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENTPIPE_PARAM_DESC numaralandırması'
title: COR_PRF_EVENTPIPE_PARAM_DESC numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_DESC
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: b23897580092cc9f3f887a21e86f7111fecd9f19
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805798"
---
# <a name="cor_prf_eventpipe_param_desc-enumeration"></a><span data-ttu-id="e5951-103">COR_PRF_EVENTPIPE_PARAM_DESC numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e5951-103">COR_PRF_EVENTPIPE_PARAM_DESC Enumeration</span></span>

<span data-ttu-id="e5951-104">Bir EventPipe olayının parametre adını ve türünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5951-104">Describes the parameter name and type for an EventPipe event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e5951-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5951-105">Syntax</span></span>  
  
```cpp  
typedef struct
{
    UINT32       type;
    UINT32       elementType;
    const WCHAR *name;
} COR_PRF_EVENTPIPE_PARAM_DESC;
```  
  
## <a name="members"></a><span data-ttu-id="e5951-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e5951-106">Members</span></span>  
  
|<span data-ttu-id="e5951-107">Üye</span><span class="sxs-lookup"><span data-stu-id="e5951-107">Member</span></span>|<span data-ttu-id="e5951-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5951-108">Description</span></span>|  
|------------|-----------------|  
|`type`|<span data-ttu-id="e5951-109">Parametrenin türü.</span><span class="sxs-lookup"><span data-stu-id="e5951-109">The type of the parameter.</span></span>|  
|`elementType`|<span data-ttu-id="e5951-110">Bu parametre bir dizi türü ise öğe türü.</span><span class="sxs-lookup"><span data-stu-id="e5951-110">The element type if this parameter is an array type.</span></span>|  
|`name`|<span data-ttu-id="e5951-111">Parametrenin adını içeren geniş bir karakter dizesi.</span><span class="sxs-lookup"><span data-stu-id="e5951-111">A wide character string containing the name of the parameter.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5951-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5951-112">Remarks</span></span>  

 <span data-ttu-id="e5951-113">`COR_PRF_EVENTPIPE_PARAM_DESC`Yapı, tanımlanmakta olan olayın parametre türlerini tanımlamak Için [ICorProfilerInfo12:: EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5951-113">The `COR_PRF_EVENTPIPE_PARAM_DESC` structure is used by the [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) method to define the parameter types of the event being defined.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="e5951-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5951-114">Requirements</span></span>  

<span data-ttu-id="e5951-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e5951-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="e5951-116">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5951-116">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e5951-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5951-117">See also</span></span>

- [<span data-ttu-id="e5951-118">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="e5951-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="e5951-119">ICorProfilerInfo12:: EventPipeDefineEvent</span><span class="sxs-lookup"><span data-stu-id="e5951-119">ICorProfilerInfo12::EventPipeDefineEvent</span></span>](icorprofilerinfo12-eventpipedefineevent-method.md)

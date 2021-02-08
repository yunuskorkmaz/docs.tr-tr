---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_REJIT_FLAGS numaralandırması'
title: COR_PRF_REJIT_FLAGS Sabit Listesi
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: a27b6d90b51254560f25fbadb18ac95fe838ab2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789027"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="4f8c4-103">COR_PRF_REJIT_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4f8c4-103">COR_PRF_REJIT_FLAGS Enumeration</span></span>

<span data-ttu-id="4f8c4-104">[ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API 'sinin nasıl davrandığını belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-104">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f8c4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4f8c4-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4f8c4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4f8c4-106">Members</span></span>  
  
|<span data-ttu-id="4f8c4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="4f8c4-107">Member</span></span>|<span data-ttu-id="4f8c4-108">Description</span><span class="sxs-lookup"><span data-stu-id="4f8c4-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="4f8c4-109">Yeniden derlenen yöntemlerin diğer metotlarda satır içine alınmış olması engellenir.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-109">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="4f8c4-110">`GetFunctionParameters`Yeniden derleme yapmak istenen yöntemlerin satır içi yöntemler için geri çağrılar alın.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-110">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="4f8c4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f8c4-111">Requirements</span></span>  

 <span data-ttu-id="4f8c4-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="4f8c4-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="4f8c4-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4f8c4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f8c4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4f8c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f8c4-115">**.NET Framework sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f8c4-115">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f8c4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-116">See also</span></span>

- [<span data-ttu-id="4f8c4-117">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="4f8c4-117">Profiling Enumerations</span></span>](profiling-enumerations.md)

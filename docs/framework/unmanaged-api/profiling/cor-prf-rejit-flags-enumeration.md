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
ms.openlocfilehash: aad66285e9b31558a68b8ccdfc71f103d1772946
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106923"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="80ce4-103">COR_PRF_REJIT_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="80ce4-103">COR_PRF_REJIT_FLAGS Enumeration</span></span>

<span data-ttu-id="80ce4-104">[ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API 'sinin nasıl davrandığını belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="80ce4-104">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ce4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="80ce4-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="80ce4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="80ce4-106">Members</span></span>  
  
|<span data-ttu-id="80ce4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="80ce4-107">Member</span></span>|<span data-ttu-id="80ce4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80ce4-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="80ce4-109">Yeniden derlenen yöntemlerin diğer metotlarda satır içine alınmış olması engellenir.</span><span class="sxs-lookup"><span data-stu-id="80ce4-109">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="80ce4-110">`GetFunctionParameters`Yeniden derleme yapmak istenen yöntemlerin satır içi yöntemler için geri çağrılar alın.</span><span class="sxs-lookup"><span data-stu-id="80ce4-110">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="80ce4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80ce4-111">Requirements</span></span>  

 <span data-ttu-id="80ce4-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="80ce4-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="80ce4-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="80ce4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80ce4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="80ce4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80ce4-115">**.NET Framework sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ce4-115">**.NET Framework Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="80ce4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80ce4-116">See also</span></span>

- [<span data-ttu-id="80ce4-117">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="80ce4-117">Profiling Enumerations</span></span>](profiling-enumerations.md)

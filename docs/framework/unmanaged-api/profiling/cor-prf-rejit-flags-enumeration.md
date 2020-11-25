---
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
ms.openlocfilehash: 09349674e0cf80649cc948e25a1c476c6f8097e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716375"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="7ff99-102">COR_PRF_REJIT_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7ff99-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>

<span data-ttu-id="7ff99-103">[ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API 'sinin nasıl davrandığını belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ff99-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff99-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ff99-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7ff99-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7ff99-105">Members</span></span>  
  
|<span data-ttu-id="7ff99-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7ff99-106">Member</span></span>|<span data-ttu-id="7ff99-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ff99-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="7ff99-108">Yeniden derlenen yöntemlerin diğer metotlarda satır içine alınmış olması engellenir.</span><span class="sxs-lookup"><span data-stu-id="7ff99-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="7ff99-109">`GetFunctionParameters`Yeniden derleme yapmak istenen yöntemlerin satır içi yöntemler için geri çağrılar alın.</span><span class="sxs-lookup"><span data-stu-id="7ff99-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="7ff99-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ff99-110">Requirements</span></span>  

 <span data-ttu-id="7ff99-111">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="7ff99-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="7ff99-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7ff99-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ff99-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7ff99-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ff99-114">**.NET Framework sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff99-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7ff99-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff99-115">See also</span></span>

- [<span data-ttu-id="7ff99-116">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7ff99-116">Profiling Enumerations</span></span>](profiling-enumerations.md)

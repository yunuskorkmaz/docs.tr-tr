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
ms.openlocfilehash: fabbcd497dc2f321da90188cebbac6ed4e147492
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867093"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="e0809-102">COR_PRF_REJIT_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e0809-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="e0809-103">[ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API 'sinin nasıl davrandığını belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e0809-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0809-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0809-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e0809-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e0809-105">Members</span></span>  
  
|<span data-ttu-id="e0809-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e0809-106">Member</span></span>|<span data-ttu-id="e0809-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0809-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="e0809-108">Yeniden derlenen yöntemlerin diğer metotlarda satır içine alınmış olması engellenir.</span><span class="sxs-lookup"><span data-stu-id="e0809-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="e0809-109">Yeniden derlenen yöntemlerin satır içi tüm yöntemler için `GetFunctionParameters` geri çağırmaları alın.</span><span class="sxs-lookup"><span data-stu-id="e0809-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="e0809-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0809-110">Requirements</span></span>  
 <span data-ttu-id="e0809-111">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e0809-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
  
 <span data-ttu-id="e0809-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e0809-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0809-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e0809-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0809-114">**.NET Framework sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0809-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="e0809-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0809-115">See also</span></span>

- [<span data-ttu-id="e0809-116">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e0809-116">Profiling Enumerations</span></span>](profiling-enumerations.md)

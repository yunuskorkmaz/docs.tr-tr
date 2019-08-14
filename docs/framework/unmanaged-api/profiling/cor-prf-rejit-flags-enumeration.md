---
title: COR_PRF_REJIT_FLAGS numaralandırması
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
ms.openlocfilehash: c616cb45eadab3a55aa76526d530cb2841e6d5fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973782"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="b2443-102">COR_PRF_REJIT_FLAGS numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b2443-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="b2443-103">[ICorProfilerInfo10:: RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md) API 'sinin nasıl davrandığını belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b2443-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2443-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2443-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b2443-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b2443-105">Members</span></span>  
  
|<span data-ttu-id="b2443-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b2443-106">Member</span></span>|<span data-ttu-id="b2443-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2443-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="b2443-108">Yeniden derlenen yöntemlerin diğer metotlarda satır içine alınmış olması engellenir.</span><span class="sxs-lookup"><span data-stu-id="b2443-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="b2443-109">Yeniden `GetFunctionParameters` derleme yapmak istenen yöntemlerin satır içi yöntemler için geri çağrılar alın.</span><span class="sxs-lookup"><span data-stu-id="b2443-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="b2443-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2443-110">Requirements</span></span>  
 <span data-ttu-id="b2443-111">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="b2443-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="b2443-112">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b2443-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2443-113">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2443-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2443-114">**.NET Framework sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2443-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="b2443-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2443-115">See also</span></span>

- [<span data-ttu-id="b2443-116">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b2443-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

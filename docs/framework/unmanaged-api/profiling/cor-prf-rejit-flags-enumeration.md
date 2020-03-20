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
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177095"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="c815b-102">COR_PRF_REJIT_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c815b-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="c815b-103">[ICorProfilerInfo10::RequestReJITWithLiners](icorprofilerinfo10-requestrejitwithinliners-method.md) API'nin nasıl olması gerektiğini gösteren değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="c815b-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c815b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c815b-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c815b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c815b-105">Members</span></span>  
  
|<span data-ttu-id="c815b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c815b-106">Member</span></span>|<span data-ttu-id="c815b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c815b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="c815b-108">ReJITted yöntemleri diğer yöntemlerde inlined olması engellenir.</span><span class="sxs-lookup"><span data-stu-id="c815b-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="c815b-109">Yeniden `GetFunctionParameters` canlandırılmak istenen yöntemlerin satır satırını gösteren yöntemler için geri arama alın.</span><span class="sxs-lookup"><span data-stu-id="c815b-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="c815b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c815b-110">Requirements</span></span>  
 <span data-ttu-id="c815b-111">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri.](../../../core/install/dependencies.md?pivots=os-windows)</span><span class="sxs-lookup"><span data-stu-id="c815b-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="c815b-112">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c815b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c815b-113">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c815b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c815b-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c815b-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c815b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c815b-115">See also</span></span>

- [<span data-ttu-id="c815b-116">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c815b-116">Profiling Enumerations</span></span>](profiling-enumerations.md)

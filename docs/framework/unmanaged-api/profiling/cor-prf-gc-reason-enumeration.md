---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_GC_REASON numaralandırması'
title: COR_PRF_GC_REASON Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
ms.openlocfilehash: f5c8201f2023e07f9bb9d540f6d5f8fca1c19419
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648812"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="203ef-103">COR_PRF_GC_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="203ef-103">COR_PRF_GC_REASON Enumeration</span></span>

<span data-ttu-id="203ef-104">Çöp toplamanın oluşma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="203ef-104">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203ef-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="203ef-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="203ef-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="203ef-106">Members</span></span>  
  
|<span data-ttu-id="203ef-107">Üye</span><span class="sxs-lookup"><span data-stu-id="203ef-107">Member</span></span>|<span data-ttu-id="203ef-108">Description</span><span class="sxs-lookup"><span data-stu-id="203ef-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="203ef-109">Çöp toplama bir yöntem tarafından oluşturuldu <xref:System.GC.Collect%2A> .</span><span class="sxs-lookup"><span data-stu-id="203ef-109">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="203ef-110">Neden belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="203ef-110">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="203ef-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="203ef-111">Requirements</span></span>  

 <span data-ttu-id="203ef-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="203ef-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="203ef-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="203ef-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="203ef-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="203ef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="203ef-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="203ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203ef-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="203ef-116">See also</span></span>

- [<span data-ttu-id="203ef-117">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="203ef-117">Profiling Enumerations</span></span>](profiling-enumerations.md)

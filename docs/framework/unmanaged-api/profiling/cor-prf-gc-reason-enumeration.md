---
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
ms.openlocfilehash: f41f00a9699d6fc135ca3b9c0b4b470ca0359279
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682399"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="fe8b2-102">COR_PRF_GC_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fe8b2-102">COR_PRF_GC_REASON Enumeration</span></span>

<span data-ttu-id="fe8b2-103">Çöp toplamanın oluşma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe8b2-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe8b2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe8b2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="fe8b2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fe8b2-105">Members</span></span>  
  
|<span data-ttu-id="fe8b2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fe8b2-106">Member</span></span>|<span data-ttu-id="fe8b2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe8b2-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="fe8b2-108">Çöp toplama bir yöntem tarafından oluşturuldu <xref:System.GC.Collect%2A> .</span><span class="sxs-lookup"><span data-stu-id="fe8b2-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="fe8b2-109">Neden belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="fe8b2-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe8b2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe8b2-110">Requirements</span></span>  

 <span data-ttu-id="fe8b2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe8b2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe8b2-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fe8b2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe8b2-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe8b2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe8b2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe8b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe8b2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe8b2-115">See also</span></span>

- [<span data-ttu-id="fe8b2-116">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="fe8b2-116">Profiling Enumerations</span></span>](profiling-enumerations.md)

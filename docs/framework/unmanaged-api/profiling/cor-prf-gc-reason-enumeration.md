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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: daf97f25b1adc30b173fcd81812a4b197915cdd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196950"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="159ca-102">COR_PRF_GC_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="159ca-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="159ca-103">Çöp toplama oluştuğu nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="159ca-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="159ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="159ca-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="159ca-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="159ca-105">Members</span></span>  
  
|<span data-ttu-id="159ca-106">Üye</span><span class="sxs-lookup"><span data-stu-id="159ca-106">Member</span></span>|<span data-ttu-id="159ca-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="159ca-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="159ca-108">Çöp toplama tarafından başlattığı bir <xref:System.GC.Collect%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="159ca-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="159ca-109">Bunun nedeni büyük/küçük harf belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="159ca-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="159ca-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="159ca-110">Requirements</span></span>  
 <span data-ttu-id="159ca-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="159ca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="159ca-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="159ca-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="159ca-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="159ca-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="159ca-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="159ca-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="159ca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="159ca-115">See also</span></span>

- [<span data-ttu-id="159ca-116">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="159ca-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

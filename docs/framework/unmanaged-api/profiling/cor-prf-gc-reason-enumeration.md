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
ms.openlocfilehash: 13740920e8db5d44b71cd3c324742945c64b3e59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498966"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="16e21-102">COR_PRF_GC_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="16e21-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="16e21-103">Çöp toplama oluştuğu nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16e21-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16e21-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="16e21-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="16e21-105">Members</span></span>  
  
|<span data-ttu-id="16e21-106">Üye</span><span class="sxs-lookup"><span data-stu-id="16e21-106">Member</span></span>|<span data-ttu-id="16e21-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16e21-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="16e21-108">Çöp toplama tarafından başlattığı bir <xref:System.GC.Collect%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="16e21-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="16e21-109">Bunun nedeni büyük/küçük harf belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="16e21-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16e21-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16e21-110">Requirements</span></span>  
 <span data-ttu-id="16e21-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16e21-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16e21-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="16e21-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16e21-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16e21-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16e21-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16e21-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16e21-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16e21-115">See also</span></span>
- [<span data-ttu-id="16e21-116">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="16e21-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

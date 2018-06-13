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
ms.openlocfilehash: 63f6ea4a348b3035a1f0b1d3e00f61f689915fa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450105"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="60c30-102">COR_PRF_GC_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="60c30-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="60c30-103">Çöp toplama oluştuğunu nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="60c30-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60c30-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="60c30-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="60c30-105">Members</span></span>  
  
|<span data-ttu-id="60c30-106">Üye</span><span class="sxs-lookup"><span data-stu-id="60c30-106">Member</span></span>|<span data-ttu-id="60c30-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60c30-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="60c30-108">Çöp toplama tarafından kopyaladığınızda bir <xref:System.GC.Collect%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="60c30-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="60c30-109">Neden belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="60c30-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60c30-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60c30-110">Requirements</span></span>  
 <span data-ttu-id="60c30-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60c30-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c30-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60c30-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60c30-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60c30-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60c30-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c30-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60c30-115">See Also</span></span>  
 [<span data-ttu-id="60c30-116">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="60c30-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

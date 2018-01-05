---
title: "COR_PRF_RUNTIME_TYPE Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_RUNTIME_TYPE Enumeration
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_RUNTIME_TYPE
helpviewer_keywords: COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 154773e76046656e4286f4ba12717b6b45e9b069
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="8ee08-102">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8ee08-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="8ee08-103">Ortak dil çalışma zamanı (CLR) sürümünü gösteren değerler içerir: Masaüstü veya Silverlight kullanılan CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="8ee08-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ee08-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="8ee08-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8ee08-105">Members</span></span>  
  
|<span data-ttu-id="8ee08-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8ee08-106">Member</span></span>|<span data-ttu-id="8ee08-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ee08-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="8ee08-108">CLR Masaüstü sürümü.</span><span class="sxs-lookup"><span data-stu-id="8ee08-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="8ee08-109">Silverlight kullanılan CLR çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="8ee08-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ee08-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ee08-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ee08-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ee08-111">Requirements</span></span>  
 <span data-ttu-id="8ee08-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee08-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee08-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ee08-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ee08-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ee08-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ee08-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ee08-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee08-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ee08-116">See Also</span></span>  
 [<span data-ttu-id="8ee08-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8ee08-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

---
title: "COR_PRF_JIT_CACHE Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_JIT_CACHE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_JIT_CACHE
helpviewer_keywords: COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08fe81321e958d61c1aae86ae366077b563dba3e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="014b7-102">COR_PRF_JIT_CACHE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="014b7-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="014b7-103">Önbelleğe alınan işlevi arama sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="014b7-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="014b7-104">`COR_PRF_CACHED_FUNCTION_FOUND`Bu nedenle sıfır değerine sahip `COR_PRF_JIT_CACHE` Boolean bir yedek kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="014b7-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="014b7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="014b7-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="014b7-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="014b7-106">Members</span></span>  
  
|<span data-ttu-id="014b7-107">Üye</span><span class="sxs-lookup"><span data-stu-id="014b7-107">Member</span></span>|<span data-ttu-id="014b7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="014b7-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="014b7-109">Arama işlevi bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="014b7-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="014b7-110">Arama işlevini bulamadı.</span><span class="sxs-lookup"><span data-stu-id="014b7-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="014b7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="014b7-111">Requirements</span></span>  
 <span data-ttu-id="014b7-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="014b7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="014b7-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="014b7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="014b7-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="014b7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="014b7-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="014b7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014b7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="014b7-116">See Also</span></span>  
 [<span data-ttu-id="014b7-117">Profil oluşturma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="014b7-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

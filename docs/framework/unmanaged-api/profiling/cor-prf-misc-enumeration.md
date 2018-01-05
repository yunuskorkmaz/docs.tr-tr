---
title: "COR_PRF_MISC Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_MISC
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_MISC
helpviewer_keywords: COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da858ecf9fc002061d663e8c8f4d4036ef134d5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="cbcf9-102">COR_PRF_MISC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cbcf9-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="cbcf9-103">Özel tanımlayıcılarını belirtmek sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cbcf9-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbcf9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbcf9-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="cbcf9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cbcf9-105">Members</span></span>  
  
|<span data-ttu-id="cbcf9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cbcf9-106">Member</span></span>|<span data-ttu-id="cbcf9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbcf9-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="cbcf9-108">Tarafından kullanılan varsayılan tanımlayıcısı [Icorprofilerınfo::getmoduleınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) henüz bir derlemeye bağlı olmayan bir modül için.</span><span class="sxs-lookup"><span data-stu-id="cbcf9-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="cbcf9-109">Bir sınıfa ait değil global sabitler için varsayılan sınıf tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="cbcf9-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="cbcf9-110">Bir modüle ait değil genel nesneler için varsayılan modülü tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="cbcf9-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cbcf9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbcf9-111">Requirements</span></span>  
 <span data-ttu-id="cbcf9-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbcf9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbcf9-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cbcf9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cbcf9-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbcf9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbcf9-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbcf9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbcf9-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbcf9-116">See Also</span></span>  
 [<span data-ttu-id="cbcf9-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cbcf9-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

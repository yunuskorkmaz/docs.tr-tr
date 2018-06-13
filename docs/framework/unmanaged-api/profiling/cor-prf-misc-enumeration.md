---
title: COR_PRF_MISC Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8f4cffd718fffa9145e1082092ecec45b80a2ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451065"
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="62f22-102">COR_PRF_MISC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="62f22-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="62f22-103">Özel tanımlayıcılarını belirtmek sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="62f22-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62f22-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="62f22-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="62f22-105">Members</span></span>  
  
|<span data-ttu-id="62f22-106">Üye</span><span class="sxs-lookup"><span data-stu-id="62f22-106">Member</span></span>|<span data-ttu-id="62f22-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62f22-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="62f22-108">Tarafından kullanılan varsayılan tanımlayıcısı [Icorprofilerınfo::getmoduleınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) henüz bir derlemeye bağlı olmayan bir modül için.</span><span class="sxs-lookup"><span data-stu-id="62f22-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="62f22-109">Bir sınıfa ait değil global sabitler için varsayılan sınıf tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="62f22-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="62f22-110">Bir modüle ait değil genel nesneler için varsayılan modülü tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="62f22-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62f22-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62f22-111">Requirements</span></span>  
 <span data-ttu-id="62f22-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f22-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f22-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62f22-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62f22-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62f22-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62f22-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f22-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f22-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62f22-116">See Also</span></span>  
 [<span data-ttu-id="62f22-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="62f22-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

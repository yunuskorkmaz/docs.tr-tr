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
ms.openlocfilehash: 3b40ac5f49288f7b30018e0c8c727e3ce6b73ae8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199498"
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="b5f47-102">COR_PRF_MISC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b5f47-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="b5f47-103">Özel tanımlayıcılardır belirten sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b5f47-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f47-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5f47-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="b5f47-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b5f47-105">Members</span></span>  
  
|<span data-ttu-id="b5f47-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b5f47-106">Member</span></span>|<span data-ttu-id="b5f47-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5f47-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="b5f47-108">Tarafından kullanılan varsayılan tanımlayıcısı [Icorprofilerınfo::getmoduleınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) henüz bir derlemeye bağlı olmayan bir modül için.</span><span class="sxs-lookup"><span data-stu-id="b5f47-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="b5f47-109">Bir sınıfa ait olmayan global sabitler için varsayılan sınıf tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b5f47-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="b5f47-110">Bir modüle ait olmayan, genel nesneler için varsayılan modülü tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="b5f47-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5f47-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5f47-111">Requirements</span></span>  
 <span data-ttu-id="b5f47-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5f47-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f47-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5f47-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5f47-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5f47-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5f47-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5f47-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f47-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5f47-116">See also</span></span>

- [<span data-ttu-id="b5f47-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b5f47-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

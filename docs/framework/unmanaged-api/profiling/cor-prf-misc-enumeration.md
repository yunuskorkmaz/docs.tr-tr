---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_MISC numaralandırması'
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
ms.openlocfilehash: 037ea040dfdf9f5be48369ab4d8e94b12aea51ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687603"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="e9c63-103">COR_PRF_MISC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e9c63-103">COR_PRF_MISC Enumeration</span></span>

<span data-ttu-id="e9c63-104">Özel tanımlayıcılar belirten sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e9c63-104">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c63-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e9c63-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="e9c63-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e9c63-106">Members</span></span>  
  
|<span data-ttu-id="e9c63-107">Üye</span><span class="sxs-lookup"><span data-stu-id="e9c63-107">Member</span></span>|<span data-ttu-id="e9c63-108">Description</span><span class="sxs-lookup"><span data-stu-id="e9c63-108">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="e9c63-109">Henüz bir derlemeye eklenmemiş bir modül için [ICorProfilerInfo:: GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) tarafından kullanılan varsayılan tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="e9c63-109">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="e9c63-110">Bir sınıfa ait olmayan genel sabitler için varsayılan sınıf tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e9c63-110">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="e9c63-111">Bir modüle ait olmayan genel nesneler için varsayılan modül tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e9c63-111">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9c63-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9c63-112">Requirements</span></span>  

 <span data-ttu-id="e9c63-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9c63-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9c63-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e9c63-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9c63-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e9c63-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9c63-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9c63-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c63-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9c63-117">See also</span></span>

- [<span data-ttu-id="e9c63-118">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="e9c63-118">Profiling Enumerations</span></span>](profiling-enumerations.md)

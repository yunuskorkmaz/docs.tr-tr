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
ms.openlocfilehash: 7b8f2845589a8372f62c95ef1a82eae3ed602c1f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500838"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="ec180-102">COR_PRF_MISC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ec180-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="ec180-103">Özel tanımlayıcılar belirten sabit değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ec180-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec180-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec180-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="ec180-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ec180-105">Members</span></span>  
  
|<span data-ttu-id="ec180-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ec180-106">Member</span></span>|<span data-ttu-id="ec180-107">Description</span><span class="sxs-lookup"><span data-stu-id="ec180-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="ec180-108">Henüz bir derlemeye eklenmemiş bir modül için [ICorProfilerInfo:: GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) tarafından kullanılan varsayılan tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="ec180-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="ec180-109">Bir sınıfa ait olmayan genel sabitler için varsayılan sınıf tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ec180-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="ec180-110">Bir modüle ait olmayan genel nesneler için varsayılan modül tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ec180-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec180-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec180-111">Requirements</span></span>  
 <span data-ttu-id="ec180-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec180-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec180-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ec180-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec180-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ec180-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec180-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec180-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec180-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec180-116">See also</span></span>

- [<span data-ttu-id="ec180-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ec180-117">Profiling Enumerations</span></span>](profiling-enumerations.md)

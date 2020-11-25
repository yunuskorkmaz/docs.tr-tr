---
title: COR_PRF_RUNTIME_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
ms.openlocfilehash: b599a97f414491ff80000f99551a727b86ae13de
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696758"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="ab734-102">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ab734-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>

<span data-ttu-id="ab734-103">Silverlight 'ta kullanılan ortak dil çalışma zamanının (CLR) sürümünü (masaüstü veya CoreCLR) gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ab734-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab734-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab734-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="ab734-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ab734-105">Members</span></span>  
  
|<span data-ttu-id="ab734-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ab734-106">Member</span></span>|<span data-ttu-id="ab734-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab734-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="ab734-108">CLR masaüstü sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab734-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="ab734-109">Silverlight 'ta kullanılan CLR 'nin çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab734-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab734-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab734-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab734-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab734-111">Requirements</span></span>  

 <span data-ttu-id="ab734-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab734-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab734-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ab734-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab734-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ab734-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab734-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab734-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab734-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab734-116">See also</span></span>

- [<span data-ttu-id="ab734-117">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ab734-117">Profiling Enumerations</span></span>](profiling-enumerations.md)

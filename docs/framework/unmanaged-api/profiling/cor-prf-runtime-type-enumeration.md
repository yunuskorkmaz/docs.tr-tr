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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c52f96ad9458dfd5cdedc5cc73154aa570c6759
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751968"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="8784a-102">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8784a-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="8784a-103">Ortak dil çalışma zamanı (CLR) sürümünü gösteren değerleri içerir: Masaüstü veya Silverlight'ta kullanılan CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="8784a-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8784a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8784a-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="8784a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8784a-105">Members</span></span>  
  
|<span data-ttu-id="8784a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8784a-106">Member</span></span>|<span data-ttu-id="8784a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8784a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="8784a-108">CLR Masaüstü sürümü.</span><span class="sxs-lookup"><span data-stu-id="8784a-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="8784a-109">Silverlight'ta kullanılan CLR, çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="8784a-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8784a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8784a-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8784a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8784a-111">Requirements</span></span>  
 <span data-ttu-id="8784a-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8784a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8784a-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8784a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8784a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8784a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8784a-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8784a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8784a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8784a-116">See also</span></span>

- [<span data-ttu-id="8784a-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8784a-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

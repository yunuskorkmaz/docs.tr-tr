---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_RUNTIME_TYPE numaralandırması'
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
ms.openlocfilehash: 8f4b4a0c51c43b1db97b511387eaee1aee79f523
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789053"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="d6bad-103">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d6bad-103">COR_PRF_RUNTIME_TYPE Enumeration</span></span>

<span data-ttu-id="d6bad-104">Silverlight 'ta kullanılan ortak dil çalışma zamanının (CLR) sürümünü (masaüstü veya CoreCLR) gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d6bad-104">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6bad-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d6bad-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="d6bad-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d6bad-106">Members</span></span>  
  
|<span data-ttu-id="d6bad-107">Üye</span><span class="sxs-lookup"><span data-stu-id="d6bad-107">Member</span></span>|<span data-ttu-id="d6bad-108">Description</span><span class="sxs-lookup"><span data-stu-id="d6bad-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="d6bad-109">CLR masaüstü sürümü.</span><span class="sxs-lookup"><span data-stu-id="d6bad-109">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="d6bad-110">Silverlight 'ta kullanılan CLR 'nin çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="d6bad-110">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6bad-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6bad-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6bad-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6bad-112">Requirements</span></span>  

 <span data-ttu-id="d6bad-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6bad-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6bad-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d6bad-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6bad-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d6bad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6bad-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6bad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6bad-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6bad-117">See also</span></span>

- [<span data-ttu-id="d6bad-118">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d6bad-118">Profiling Enumerations</span></span>](profiling-enumerations.md)

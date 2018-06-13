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
ms.openlocfilehash: 28e6e95bbcca35ad39f30adcf100519748c02838
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450004"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="ff453-102">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ff453-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="ff453-103">Ortak dil çalışma zamanı (CLR) sürümünü gösteren değerler içerir: Masaüstü veya Silverlight kullanılan CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ff453-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff453-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff453-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="ff453-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ff453-105">Members</span></span>  
  
|<span data-ttu-id="ff453-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ff453-106">Member</span></span>|<span data-ttu-id="ff453-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff453-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="ff453-108">CLR Masaüstü sürümü.</span><span class="sxs-lookup"><span data-stu-id="ff453-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="ff453-109">Silverlight kullanılan CLR çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="ff453-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff453-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff453-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff453-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff453-111">Requirements</span></span>  
 <span data-ttu-id="ff453-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff453-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff453-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff453-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff453-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff453-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff453-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff453-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff453-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff453-116">See Also</span></span>  
 [<span data-ttu-id="ff453-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ff453-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

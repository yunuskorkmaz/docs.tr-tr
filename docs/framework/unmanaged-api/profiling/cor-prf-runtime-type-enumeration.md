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
ms.openlocfilehash: e57c622780f0bc92061fd2928ea861f904d9eb37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599188"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="fff7e-102">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fff7e-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="fff7e-103">Ortak dil çalışma zamanı (CLR) sürümünü gösteren değerleri içerir: Masaüstü veya Silverlight'ta kullanılan CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fff7e-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff7e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fff7e-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="fff7e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fff7e-105">Members</span></span>  
  
|<span data-ttu-id="fff7e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fff7e-106">Member</span></span>|<span data-ttu-id="fff7e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fff7e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="fff7e-108">CLR Masaüstü sürümü.</span><span class="sxs-lookup"><span data-stu-id="fff7e-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="fff7e-109">Silverlight'ta kullanılan CLR, çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="fff7e-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fff7e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fff7e-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff7e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fff7e-111">Requirements</span></span>  
 <span data-ttu-id="fff7e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fff7e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff7e-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fff7e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fff7e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fff7e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fff7e-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fff7e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff7e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fff7e-116">See also</span></span>

- [<span data-ttu-id="fff7e-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fff7e-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

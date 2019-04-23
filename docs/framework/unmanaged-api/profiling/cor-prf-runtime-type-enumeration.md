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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122115"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="c43af-102">COR_PRF_RUNTIME_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c43af-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="c43af-103">Ortak dil çalışma zamanı (CLR) sürümünü gösteren değerleri içerir: Masaüstü veya Silverlight'ta kullanılan CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c43af-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c43af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c43af-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="c43af-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c43af-105">Members</span></span>  
  
|<span data-ttu-id="c43af-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c43af-106">Member</span></span>|<span data-ttu-id="c43af-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c43af-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="c43af-108">CLR Masaüstü sürümü.</span><span class="sxs-lookup"><span data-stu-id="c43af-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="c43af-109">Silverlight'ta kullanılan CLR, çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="c43af-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c43af-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c43af-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c43af-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c43af-111">Requirements</span></span>  
 <span data-ttu-id="c43af-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c43af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c43af-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c43af-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c43af-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c43af-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c43af-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c43af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43af-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c43af-116">See also</span></span>

- [<span data-ttu-id="c43af-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c43af-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

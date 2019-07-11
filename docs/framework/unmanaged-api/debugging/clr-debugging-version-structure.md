---
title: CLR_DEBUGGING_VERSION Yapısı
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e71a1538e42061c6cb949b22bb63fe6b17a0dfc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741111"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="e75c2-102">CLR_DEBUGGING_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="e75c2-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="e75c2-103">Ürün sürümü, hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e75c2-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e75c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e75c2-104">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="e75c2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e75c2-105">Members</span></span>  
  
|<span data-ttu-id="e75c2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e75c2-106">Member</span></span>|<span data-ttu-id="e75c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e75c2-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="e75c2-108">Yapı sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="e75c2-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="e75c2-109">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="e75c2-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="e75c2-110">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="e75c2-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="e75c2-111">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="e75c2-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="e75c2-112">Düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="e75c2-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e75c2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e75c2-113">Remarks</span></span>  
 <span data-ttu-id="e75c2-114">`CLR_DEBUGGING_VERSION` Yapısıdır cor_versıon yapısı ile aynı ancak, `CLR_DEBUGGING_VERSION` yapısı bir ek yapı sürümü alanı sağlar (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="e75c2-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="e75c2-115">Şu anda, bu alan, sıfır olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e75c2-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e75c2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e75c2-116">Requirements</span></span>  
 <span data-ttu-id="e75c2-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e75c2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e75c2-118">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="e75c2-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e75c2-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e75c2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e75c2-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e75c2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75c2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e75c2-121">See also</span></span>

- [<span data-ttu-id="e75c2-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e75c2-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="e75c2-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e75c2-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

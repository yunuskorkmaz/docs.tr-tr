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
ms.openlocfilehash: a4049b0ed25d4c0fda00fe9b0dad5887fa4f6996
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506946"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="6a78a-102">CLR_DEBUGGING_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="6a78a-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="6a78a-103">Ürün sürümü, hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a78a-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a78a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a78a-104">Syntax</span></span>  
  
```  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="6a78a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6a78a-105">Members</span></span>  
  
|<span data-ttu-id="6a78a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6a78a-106">Member</span></span>|<span data-ttu-id="6a78a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a78a-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="6a78a-108">Yapı sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="6a78a-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="6a78a-109">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="6a78a-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="6a78a-110">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="6a78a-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="6a78a-111">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="6a78a-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="6a78a-112">Düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="6a78a-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a78a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a78a-113">Remarks</span></span>  
 <span data-ttu-id="6a78a-114">`CLR_DEBUGGING_VERSION` Yapısıdır cor_versıon yapısı ile aynı ancak, `CLR_DEBUGGING_VERSION` yapısı bir ek yapı sürümü alanı sağlar (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="6a78a-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="6a78a-115">Şu anda, bu alan, sıfır olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a78a-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a78a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a78a-116">Requirements</span></span>  
 <span data-ttu-id="6a78a-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a78a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a78a-118">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="6a78a-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="6a78a-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a78a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a78a-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a78a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a78a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a78a-121">See also</span></span>
- [<span data-ttu-id="6a78a-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="6a78a-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="6a78a-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6a78a-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

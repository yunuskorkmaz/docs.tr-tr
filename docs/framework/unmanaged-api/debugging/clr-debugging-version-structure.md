---
description: 'Daha fazla bilgi edinin: CLR_DEBUGGING_VERSION yapısı'
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
ms.openlocfilehash: 2d274a91948b98dc309cd5670c3dd3bf6cd01e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772789"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="cc048-103">CLR_DEBUGGING_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc048-103">CLR_DEBUGGING_VERSION Structure</span></span>

<span data-ttu-id="cc048-104">Hata ayıklama amacıyla ortak dil çalışma zamanının (CLR) ürün sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc048-104">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc048-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cc048-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cc048-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cc048-106">Members</span></span>  
  
|<span data-ttu-id="cc048-107">Üye</span><span class="sxs-lookup"><span data-stu-id="cc048-107">Member</span></span>|<span data-ttu-id="cc048-108">Description</span><span class="sxs-lookup"><span data-stu-id="cc048-108">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="cc048-109">Yapı sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="cc048-109">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="cc048-110">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="cc048-110">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="cc048-111">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="cc048-111">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="cc048-112">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="cc048-112">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="cc048-113">Düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="cc048-113">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc048-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc048-114">Remarks</span></span>  

 <span data-ttu-id="cc048-115">`CLR_DEBUGGING_VERSION`Yapı COR_VERSION yapısıyla aynıdır, ancak `CLR_DEBUGGING_VERSION` Yapı ek bir yapı sürümü alanı ( `wStructVersion` ) sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc048-115">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="cc048-116">Şu anda bu alanın sıfır olarak ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc048-116">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc048-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc048-117">Requirements</span></span>  

 <span data-ttu-id="cc048-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc048-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc048-119">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="cc048-119">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="cc048-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc048-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc048-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc048-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc048-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc048-122">See also</span></span>

- [<span data-ttu-id="cc048-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="cc048-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="cc048-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cc048-124">Debugging</span></span>](index.md)

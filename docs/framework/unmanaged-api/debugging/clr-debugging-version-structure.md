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
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132426"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="eb285-102">CLR_DEBUGGING_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="eb285-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="eb285-103">Hata ayıklama amacıyla ortak dil çalışma zamanının (CLR) ürün sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb285-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb285-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb285-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="eb285-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="eb285-105">Members</span></span>  
  
|<span data-ttu-id="eb285-106">Üye</span><span class="sxs-lookup"><span data-stu-id="eb285-106">Member</span></span>|<span data-ttu-id="eb285-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb285-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="eb285-108">Yapı sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="eb285-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="eb285-109">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="eb285-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="eb285-110">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="eb285-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="eb285-111">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="eb285-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="eb285-112">Düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="eb285-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb285-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb285-113">Remarks</span></span>  
 <span data-ttu-id="eb285-114">`CLR_DEBUGGING_VERSION` yapısı COR_VERSION yapısıyla aynıdır, ancak `CLR_DEBUGGING_VERSION` yapısı ek bir yapı sürümü alanı (`wStructVersion`) sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb285-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="eb285-115">Şu anda bu alanın sıfır olarak ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb285-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb285-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb285-116">Requirements</span></span>  
 <span data-ttu-id="eb285-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb285-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb285-118">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="eb285-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="eb285-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb285-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb285-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb285-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb285-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb285-121">See also</span></span>

- [<span data-ttu-id="eb285-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="eb285-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="eb285-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="eb285-123">Debugging</span></span>](index.md)

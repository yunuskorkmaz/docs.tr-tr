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
ms.openlocfilehash: 8a2abe847728a2bb1f1345ef73e55b58e4704001
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729817"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="fd501-102">CLR_DEBUGGING_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="fd501-102">CLR_DEBUGGING_VERSION Structure</span></span>

<span data-ttu-id="fd501-103">Hata ayıklama amacıyla ortak dil çalışma zamanının (CLR) ürün sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fd501-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd501-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd501-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fd501-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fd501-105">Members</span></span>  
  
|<span data-ttu-id="fd501-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fd501-106">Member</span></span>|<span data-ttu-id="fd501-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd501-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="fd501-108">Yapı sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="fd501-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="fd501-109">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="fd501-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="fd501-110">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="fd501-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="fd501-111">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="fd501-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="fd501-112">Düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="fd501-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd501-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd501-113">Remarks</span></span>  

 <span data-ttu-id="fd501-114">`CLR_DEBUGGING_VERSION`Yapı COR_VERSION yapısıyla aynıdır, ancak `CLR_DEBUGGING_VERSION` Yapı ek bir yapı sürümü alanı ( `wStructVersion` ) sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd501-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="fd501-115">Şu anda bu alanın sıfır olarak ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd501-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd501-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd501-116">Requirements</span></span>  

 <span data-ttu-id="fd501-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd501-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd501-118">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="fd501-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="fd501-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fd501-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd501-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd501-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd501-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd501-121">See also</span></span>

- [<span data-ttu-id="fd501-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="fd501-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fd501-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fd501-123">Debugging</span></span>](index.md)

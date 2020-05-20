---
title: BucketParameters Yapısı
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 7037065be138c369b847e7f86de7b46fc5ae601a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616885"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="0e64c-102">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="0e64c-102">BucketParameters Structure</span></span>
<span data-ttu-id="0e64c-103">Bir olayın tür adını ve olayla ilişkili geçerli özel durumun parametrelerini depolar.</span><span class="sxs-lookup"><span data-stu-id="0e64c-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e64c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0e64c-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="0e64c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0e64c-105">Members</span></span>  
  
|<span data-ttu-id="0e64c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0e64c-106">Member</span></span>|<span data-ttu-id="0e64c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e64c-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="0e64c-108">`true`, bu yapının geri kalanı geçerliyse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="0e64c-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="0e64c-109">Olay türünün adı.</span><span class="sxs-lookup"><span data-stu-id="0e64c-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="0e64c-110">Her biri olayla ilişkili geçerli özel durum için bir parametre belirten dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="0e64c-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e64c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e64c-111">Requirements</span></span>  
 <span data-ttu-id="0e64c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e64c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e64c-113">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="0e64c-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0e64c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e64c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e64c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e64c-115">See also</span></span>

- [<span data-ttu-id="0e64c-116">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="0e64c-116">Hosting Structures</span></span>](hosting-structures.md)

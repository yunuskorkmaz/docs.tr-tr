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
ms.openlocfilehash: 80623bdec939b0ae5fc13008c1c4001c613ac435
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195952"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="282e2-102">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="282e2-102">BucketParameters Structure</span></span>
<span data-ttu-id="282e2-103">Bir olayın tür adını ve olayla ilişkili geçerli özel durumun parametrelerini depolar.</span><span class="sxs-lookup"><span data-stu-id="282e2-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="282e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="282e2-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="282e2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="282e2-105">Members</span></span>  
  
|<span data-ttu-id="282e2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="282e2-106">Member</span></span>|<span data-ttu-id="282e2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="282e2-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="282e2-108">`true`, bu yapının geri kalanı geçerliyse; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="282e2-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="282e2-109">Olay türünün adı.</span><span class="sxs-lookup"><span data-stu-id="282e2-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="282e2-110">Her biri olayla ilişkili geçerli özel durum için bir parametre belirten dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="282e2-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="282e2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="282e2-111">Requirements</span></span>  
 <span data-ttu-id="282e2-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="282e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="282e2-113">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="282e2-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="282e2-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="282e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="282e2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="282e2-115">See also</span></span>

- [<span data-ttu-id="282e2-116">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="282e2-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)

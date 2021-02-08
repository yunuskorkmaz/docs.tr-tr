---
description: 'Daha fazla bilgi edinin: BucketParameters yapısı'
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
ms.openlocfilehash: e2d701caa0e2374cb6b44d5fb5537f2ecc7e34fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799973"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="698f8-103">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="698f8-103">BucketParameters Structure</span></span>

<span data-ttu-id="698f8-104">Bir olayın tür adını ve olayla ilişkili geçerli özel durumun parametrelerini depolar.</span><span class="sxs-lookup"><span data-stu-id="698f8-104">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="698f8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="698f8-105">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="698f8-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="698f8-106">Members</span></span>  
  
|<span data-ttu-id="698f8-107">Üye</span><span class="sxs-lookup"><span data-stu-id="698f8-107">Member</span></span>|<span data-ttu-id="698f8-108">Description</span><span class="sxs-lookup"><span data-stu-id="698f8-108">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="698f8-109">`true`, bu yapının geri kalanı geçerliyse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="698f8-109">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="698f8-110">Olay türünün adı.</span><span class="sxs-lookup"><span data-stu-id="698f8-110">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="698f8-111">Her biri olayla ilişkili geçerli özel durum için bir parametre belirten dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="698f8-111">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="698f8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="698f8-112">Requirements</span></span>  

 <span data-ttu-id="698f8-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="698f8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="698f8-114">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="698f8-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="698f8-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="698f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698f8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="698f8-116">See also</span></span>

- [<span data-ttu-id="698f8-117">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="698f8-117">Hosting Structures</span></span>](hosting-structures.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5998ce684726b2386d8f1e05eb7eaeccf455747c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946790"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="ad846-102">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="ad846-102">BucketParameters Structure</span></span>
<span data-ttu-id="ad846-103">Olay ile ilişkili olan geçerli bir özel durum için bir olay ve parametreleri türü adını depolar.</span><span class="sxs-lookup"><span data-stu-id="ad846-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad846-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad846-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="ad846-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ad846-105">Members</span></span>  
  
|<span data-ttu-id="ad846-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ad846-106">Member</span></span>|<span data-ttu-id="ad846-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad846-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="ad846-108">`true`, bu yapının rest geçerliyse; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="ad846-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="ad846-109">Olay türü adı.</span><span class="sxs-lookup"><span data-stu-id="ad846-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="ad846-110">Her biri için geçerli özel olayla ilişkili bir parametre belirtir bir dizi dizeleri.</span><span class="sxs-lookup"><span data-stu-id="ad846-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad846-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad846-111">Requirements</span></span>  
 <span data-ttu-id="ad846-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad846-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad846-113">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="ad846-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="ad846-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad846-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad846-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad846-115">See also</span></span>

- [<span data-ttu-id="ad846-116">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="ad846-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)

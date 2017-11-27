---
title: "BucketParameters Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: BucketParameters
api_location: mscoree.dll
api_type: COM
f1_keywords: BucketParameters
helpviewer_keywords: BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7626ce6b2b6278be7cd9989718c13f7c98e4ace3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="747e3-102">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="747e3-102">BucketParameters Structure</span></span>
<span data-ttu-id="747e3-103">Olay ve parametreleri tür adını olayla ilişkili geçerli özel durumu için depolar.</span><span class="sxs-lookup"><span data-stu-id="747e3-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="747e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="747e3-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="747e3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="747e3-105">Members</span></span>  
  
|<span data-ttu-id="747e3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="747e3-106">Member</span></span>|<span data-ttu-id="747e3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="747e3-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="747e3-108">`true`, bu yapıyı kalan geçerliyse; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="747e3-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="747e3-109">Olay türü adı.</span><span class="sxs-lookup"><span data-stu-id="747e3-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="747e3-110">Her biri olay ile ilişkilendirilmiş geçerli özel durumu için bir parametre belirtir dizisi dizeleri.</span><span class="sxs-lookup"><span data-stu-id="747e3-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="747e3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="747e3-111">Requirements</span></span>  
 <span data-ttu-id="747e3-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="747e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="747e3-113">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="747e3-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="747e3-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="747e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="747e3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="747e3-115">See Also</span></span>  
 [<span data-ttu-id="747e3-116">Barındırma yapıları</span><span class="sxs-lookup"><span data-stu-id="747e3-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)

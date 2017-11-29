---
title: "CorManifestResourceFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorManifestResourceFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorManifestResourceFlags
helpviewer_keywords: CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5cdaba8b1186d1720ff8b64f50a8effc4691fe8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="c87eb-102">CorManifestResourceFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c87eb-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="c87eb-103">Bir derleme bildirimi kodlanmış kaynakları görünürlüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c87eb-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c87eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c87eb-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c87eb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c87eb-105">Members</span></span>  
  
|<span data-ttu-id="c87eb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c87eb-106">Member</span></span>|<span data-ttu-id="c87eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c87eb-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="c87eb-108">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="c87eb-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="c87eb-109">Genel kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="c87eb-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="c87eb-110">Özel kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="c87eb-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c87eb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c87eb-111">Requirements</span></span>  
 <span data-ttu-id="c87eb-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c87eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c87eb-113">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c87eb-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c87eb-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c87eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87eb-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c87eb-115">See Also</span></span>  
 [<span data-ttu-id="c87eb-116">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="c87eb-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

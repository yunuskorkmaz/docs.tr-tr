---
title: CorManifestResourceFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3d3ef78da9dd639d0f9050a8b61d1e365cd8b42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650255"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="a06b9-102">CorManifestResourceFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a06b9-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="a06b9-103">Bir derleme bildiriminde kodlanmış kaynakları görünürlüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a06b9-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a06b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a06b9-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a06b9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a06b9-105">Members</span></span>  
  
|<span data-ttu-id="a06b9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a06b9-106">Member</span></span>|<span data-ttu-id="a06b9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a06b9-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="a06b9-108">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="a06b9-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="a06b9-109">Genel kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="a06b9-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="a06b9-110">Özel kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="a06b9-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a06b9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a06b9-111">Requirements</span></span>  
 <span data-ttu-id="a06b9-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a06b9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a06b9-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a06b9-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a06b9-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a06b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a06b9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a06b9-115">See also</span></span>
- [<span data-ttu-id="a06b9-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a06b9-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

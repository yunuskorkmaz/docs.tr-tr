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
ms.openlocfilehash: 21cce26c94d26f6c079fca644a31bf83cd1a6432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440716"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="7b516-102">CorManifestResourceFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7b516-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="7b516-103">Bir derleme bildirimi kodlanmış kaynakları görünürlüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b516-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b516-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b516-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7b516-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7b516-105">Members</span></span>  
  
|<span data-ttu-id="7b516-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7b516-106">Member</span></span>|<span data-ttu-id="7b516-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b516-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="7b516-108">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7b516-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="7b516-109">Genel kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="7b516-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="7b516-110">Özel kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="7b516-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b516-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b516-111">Requirements</span></span>  
 <span data-ttu-id="7b516-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b516-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b516-113">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7b516-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7b516-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b516-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b516-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b516-115">See Also</span></span>  
 [<span data-ttu-id="7b516-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7b516-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

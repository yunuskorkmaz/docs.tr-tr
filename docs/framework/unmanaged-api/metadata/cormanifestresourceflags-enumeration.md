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
ms.openlocfilehash: 08f997e133fa6cc8769efe18e7ca06c0153f15a4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781804"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="67c73-102">CorManifestResourceFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="67c73-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="67c73-103">Bir derleme bildiriminde kodlanmış kaynakları görünürlüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="67c73-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c73-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67c73-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="67c73-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="67c73-105">Members</span></span>  
  
|<span data-ttu-id="67c73-106">Üye</span><span class="sxs-lookup"><span data-stu-id="67c73-106">Member</span></span>|<span data-ttu-id="67c73-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67c73-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="67c73-108">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="67c73-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="67c73-109">Genel kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="67c73-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="67c73-110">Özel kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="67c73-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67c73-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67c73-111">Requirements</span></span>  
 <span data-ttu-id="67c73-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67c73-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67c73-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="67c73-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="67c73-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67c73-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c73-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67c73-115">See also</span></span>

- [<span data-ttu-id="67c73-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="67c73-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

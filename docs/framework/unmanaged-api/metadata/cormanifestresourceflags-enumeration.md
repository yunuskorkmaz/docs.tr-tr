---
description: 'Daha fazla bilgi edinin: CorManifestResourceFlags numaralandırması'
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
ms.openlocfilehash: a863e1248bf5274e12fc16d2edea6b28dd493963
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784411"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="26934-103">CorManifestResourceFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="26934-103">CorManifestResourceFlags Enumeration</span></span>

<span data-ttu-id="26934-104">Bir derleme bildiriminde kodlanan kaynakların görünürlüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="26934-104">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26934-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="26934-105">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="26934-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="26934-106">Members</span></span>  
  
|<span data-ttu-id="26934-107">Üye</span><span class="sxs-lookup"><span data-stu-id="26934-107">Member</span></span>|<span data-ttu-id="26934-108">Description</span><span class="sxs-lookup"><span data-stu-id="26934-108">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="26934-109">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="26934-109">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="26934-110">Kaynaklar geneldir.</span><span class="sxs-lookup"><span data-stu-id="26934-110">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="26934-111">Kaynaklar özeldir.</span><span class="sxs-lookup"><span data-stu-id="26934-111">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26934-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26934-112">Requirements</span></span>  

 <span data-ttu-id="26934-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26934-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26934-114">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="26934-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="26934-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26934-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26934-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26934-116">See also</span></span>

- [<span data-ttu-id="26934-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="26934-117">Metadata Enumerations</span></span>](metadata-enumerations.md)

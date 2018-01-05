---
title: "CorSetENC Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSetENC
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetENC
helpviewer_keywords: CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f39a1481361377fce3f6b55cf6c7daf8c075ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="e0e9d-102">CorSetENC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e0e9d-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="e0e9d-103">Meta veri oluşturma sırasında davranışını etkilemek için kullanılan değerler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0e9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0e9d-104">Syntax</span></span>  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="e0e9d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e0e9d-105">Members</span></span>  
  
|<span data-ttu-id="e0e9d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e0e9d-106">Member</span></span>|<span data-ttu-id="e0e9d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0e9d-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="e0e9d-108">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="e0e9d-109">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="e0e9d-110">Meta verileri güncelleştirildi ancak belirteçleri taşınamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="e0e9d-111">Belirteçleri güncelleştirmeleri sırasında taşınabilmesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="e0e9d-112">Yalnızca eklemeler güncelleştirmeler oluşabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="e0e9d-113">Belirteçleri taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="e0e9d-114">Derleme artımlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="e0e9d-115">Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="e0e9d-116">İçeren `MDUpdateENC`, `MDUpdateFull` ve `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0e9d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0e9d-117">Requirements</span></span>  
 <span data-ttu-id="e0e9d-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0e9d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0e9d-119">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e0e9d-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e0e9d-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0e9d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0e9d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-121">See Also</span></span>  
 [<span data-ttu-id="e0e9d-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e0e9d-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

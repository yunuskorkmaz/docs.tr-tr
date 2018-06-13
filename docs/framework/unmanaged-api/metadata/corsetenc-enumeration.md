---
title: CorSetENC Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e09bf424a41445f7e36397775d1578cdf4e7e75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442793"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="d89a9-102">CorSetENC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d89a9-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="d89a9-103">Meta veri oluşturma sırasında davranışını etkilemek için kullanılan değerler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d89a9-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d89a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d89a9-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d89a9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d89a9-105">Members</span></span>  
  
|<span data-ttu-id="d89a9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d89a9-106">Member</span></span>|<span data-ttu-id="d89a9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d89a9-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="d89a9-108">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="d89a9-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="d89a9-109">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="d89a9-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="d89a9-110">Meta verileri güncelleştirildi ancak belirteçleri taşınamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89a9-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="d89a9-111">Belirteçleri güncelleştirmeleri sırasında taşınabilmesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89a9-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="d89a9-112">Yalnızca eklemeler güncelleştirmeler oluşabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89a9-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="d89a9-113">Belirteçleri taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="d89a9-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="d89a9-114">Derleme artımlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89a9-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="d89a9-115">Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89a9-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="d89a9-116">İçeren `MDUpdateENC`, `MDUpdateFull` ve `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="d89a9-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d89a9-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d89a9-117">Requirements</span></span>  
 <span data-ttu-id="d89a9-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d89a9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d89a9-119">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d89a9-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d89a9-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d89a9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89a9-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d89a9-121">See Also</span></span>  
 [<span data-ttu-id="d89a9-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d89a9-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

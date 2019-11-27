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
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432766"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="17d22-102">CorSetENC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="17d22-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="17d22-103">Meta veri oluşturma sırasında davranışı etkilemek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="17d22-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17d22-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="17d22-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="17d22-105">Members</span></span>  
  
|<span data-ttu-id="17d22-106">Üye</span><span class="sxs-lookup"><span data-stu-id="17d22-106">Member</span></span>|<span data-ttu-id="17d22-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17d22-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="17d22-108">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="17d22-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="17d22-109">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="17d22-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="17d22-110">Meta verilerin güncelleştirilebileceğini, belirteçlerin taşınamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d22-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="17d22-111">Simgelerin güncelleştirmeler sırasında taşınabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d22-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="17d22-112">Güncelleştirmelerin yalnızca eklemelerden oluşabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d22-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="17d22-113">Belirteçler taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="17d22-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="17d22-114">Derlemenin artımlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d22-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="17d22-115">Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d22-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="17d22-116">`MDUpdateENC`, `MDUpdateFull` ve `MDUpdateIncremental`içerir.</span><span class="sxs-lookup"><span data-stu-id="17d22-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17d22-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17d22-117">Requirements</span></span>  
 <span data-ttu-id="17d22-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17d22-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d22-119">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="17d22-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="17d22-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17d22-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d22-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17d22-121">See also</span></span>

- [<span data-ttu-id="17d22-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="17d22-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

---
description: 'Daha fazla bilgi edinin: CorSetENC Enumeration'
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
ms.openlocfilehash: 5ba3e41c10b082ceb2ce7d327f7ff7f857ca98a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707403"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="3e034-103">CorSetENC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3e034-103">CorSetENC Enumeration</span></span>

<span data-ttu-id="3e034-104">Meta veri oluşturma sırasında davranışı etkilemek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3e034-104">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e034-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3e034-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3e034-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3e034-106">Members</span></span>  
  
|<span data-ttu-id="3e034-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3e034-107">Member</span></span>|<span data-ttu-id="3e034-108">Description</span><span class="sxs-lookup"><span data-stu-id="3e034-108">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="3e034-109">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="3e034-109">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="3e034-110">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="3e034-110">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="3e034-111">Meta verilerin güncelleştirilebileceğini, belirteçlerin taşınamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e034-111">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="3e034-112">Simgelerin güncelleştirmeler sırasında taşınabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e034-112">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="3e034-113">Güncelleştirmelerin yalnızca eklemelerden oluşabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e034-113">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="3e034-114">Belirteçler taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="3e034-114">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="3e034-115">Derlemenin artımlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e034-115">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="3e034-116">Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e034-116">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="3e034-117">`MDUpdateENC`, `MDUpdateFull` Ve içerir `MDUpdateIncremental` .</span><span class="sxs-lookup"><span data-stu-id="3e034-117">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e034-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e034-118">Requirements</span></span>  

 <span data-ttu-id="3e034-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e034-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e034-120">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3e034-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3e034-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e034-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e034-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e034-122">See also</span></span>

- [<span data-ttu-id="3e034-123">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="3e034-123">Metadata Enumerations</span></span>](metadata-enumerations.md)

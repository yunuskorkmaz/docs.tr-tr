---
description: 'Daha fazla bilgi edinin: CorRefToDefCheck numaralandırması'
title: CorRefToDefCheck Numaralandırması
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: ca9d1c7ceb3d9f82ef8d5f1f54d869db64053e69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784255"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="3b9a0-103">CorRefToDefCheck Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3b9a0-103">CorRefToDefCheck Enumeration</span></span>

<span data-ttu-id="3b9a0-104">Kodu iyileştirmek için hangi başvurulan öğelerin tanımlarına dönüştürüleceğini denetleyen bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-104">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b9a0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3b9a0-105">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="3b9a0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3b9a0-106">Members</span></span>  
  
|<span data-ttu-id="3b9a0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3b9a0-107">Member</span></span>|<span data-ttu-id="3b9a0-108">Description</span><span class="sxs-lookup"><span data-stu-id="3b9a0-108">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="3b9a0-109">Tür başvurularının ve üye başvurularının tanımlara dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-109">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="3b9a0-110">Bu varsayılan değerdir ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ).</span><span class="sxs-lookup"><span data-stu-id="3b9a0-110">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="3b9a0-111">Başvurulan tüm öğelerin tanımlara dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-111">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="3b9a0-112">Başvurulan hiçbir öğenin tanımlara dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-112">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="3b9a0-113">Yalnızca tür başvurularının tür tanımlarına dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-113">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="3b9a0-114">Yalnızca üye başvurularının tanımlara dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-114">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="3b9a0-115">Diğer bir deyişle, üye başvuruları Yöntem tanımlarına veya alan tanımlarına dönüştürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-115">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b9a0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b9a0-116">Requirements</span></span>  

 <span data-ttu-id="3b9a0-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b9a0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b9a0-118">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3b9a0-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3b9a0-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b9a0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b9a0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-120">See also</span></span>

- [<span data-ttu-id="3b9a0-121">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="3b9a0-121">Metadata Enumerations</span></span>](metadata-enumerations.md)

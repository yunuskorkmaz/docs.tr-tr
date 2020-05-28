---
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
ms.openlocfilehash: ce6f5993b9c1aeb63e121b3567ee468cea1c9318
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007526"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="4984a-102">CorRefToDefCheck Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4984a-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="4984a-103">Kodu iyileştirmek için hangi başvurulan öğelerin tanımlarına dönüştürüleceğini denetleyen bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="4984a-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4984a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4984a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="4984a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4984a-105">Members</span></span>  
  
|<span data-ttu-id="4984a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4984a-106">Member</span></span>|<span data-ttu-id="4984a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4984a-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="4984a-108">Tür başvurularının ve üye başvurularının tanımlara dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4984a-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="4984a-109">Bu varsayılan değerdir ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ).</span><span class="sxs-lookup"><span data-stu-id="4984a-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="4984a-110">Başvurulan tüm öğelerin tanımlara dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4984a-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="4984a-111">Başvurulan hiçbir öğenin tanımlara dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4984a-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="4984a-112">Yalnızca tür başvurularının tür tanımlarına dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4984a-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="4984a-113">Yalnızca üye başvurularının tanımlara dönüştürülmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4984a-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="4984a-114">Diğer bir deyişle, üye başvuruları Yöntem tanımlarına veya alan tanımlarına dönüştürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="4984a-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4984a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4984a-115">Requirements</span></span>  
 <span data-ttu-id="4984a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4984a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4984a-117">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="4984a-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4984a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4984a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4984a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4984a-119">See also</span></span>

- [<span data-ttu-id="4984a-120">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="4984a-120">Metadata Enumerations</span></span>](metadata-enumerations.md)

---
title: "CorRefToDefCheck Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 366110eca3c4621866213b2c9fc4bcf99103d0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="e5e93-102">CorRefToDefCheck Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e5e93-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="e5e93-103">Hangi başvurulan öğelerin tanımlarını için kod iyileştirmek üzere dönüştürülür denetim bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5e93-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e93-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5e93-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="e5e93-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e5e93-105">Members</span></span>  
  
|<span data-ttu-id="e5e93-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e5e93-106">Member</span></span>|<span data-ttu-id="e5e93-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5e93-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="e5e93-108">Tür başvuruları ve üye başvuruları tanımlarını dönüştürülüp dönüştürülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5e93-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="e5e93-109">Bu varsayılan değerdir (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="e5e93-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="e5e93-110">Başvurulan tüm öğeleri tanımlarını dönüştürülüp dönüştürülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5e93-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="e5e93-111">Başvuruda bulunulan öğe tanımları dönüştürülüp dönüştürülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5e93-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="e5e93-112">Yalnızca tür başvuruları tür tanımı için dönüştürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5e93-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="e5e93-113">Yalnızca üye başvurular tanımlarını dönüştürülüp dönüştürülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5e93-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="e5e93-114">Diğer bir deyişle, üye başvuruları yöntemi tanımları veya alan tanımları için dönüştürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="e5e93-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5e93-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5e93-115">Requirements</span></span>  
 <span data-ttu-id="e5e93-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5e93-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e93-117">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e5e93-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e5e93-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e93-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e93-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5e93-119">See Also</span></span>  
 [<span data-ttu-id="e5e93-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e5e93-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

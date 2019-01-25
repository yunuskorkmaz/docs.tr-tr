---
title: CorThreadSafetyOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b460c2c4b0d38ec46ee9d7341de9b320a2ecaa7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594648"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="968a2-102">CorThreadSafetyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="968a2-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="968a2-103">İş parçacığı güvenliği seçeneklerini seçmek için bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="968a2-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="968a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="968a2-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="968a2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="968a2-105">Members</span></span>  
  
|<span data-ttu-id="968a2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="968a2-106">Member</span></span>|<span data-ttu-id="968a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="968a2-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="968a2-108">Varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="968a2-108">Default value.</span></span> <span data-ttu-id="968a2-109">Aynı `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="968a2-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="968a2-110">Bir Okuyucu/Yazıcı kilidi ayarlanamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="968a2-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="968a2-111">Bir Okuyucu/Yazıcı kilidi ayarlanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="968a2-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="968a2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="968a2-112">Requirements</span></span>  
 <span data-ttu-id="968a2-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="968a2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="968a2-114">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="968a2-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="968a2-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="968a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968a2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="968a2-116">See also</span></span>
- [<span data-ttu-id="968a2-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="968a2-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

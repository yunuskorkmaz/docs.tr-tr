---
title: CorArgType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorArgType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorArgType
helpviewer_keywords:
- CorArgType enumeration [.NET Framework metadata]
ms.assetid: 3c1cb268-57a0-4664-91c7-f6908ff29e32
topic_type:
- apiref
ms.openlocfilehash: ac822dda30d697cbbbcacf19eb6a57d1e5fb4c3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007955"
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="d7f0b-102">CorArgType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d7f0b-102">CorArgType Enumeration</span></span>
<span data-ttu-id="d7f0b-103">Çalışma zamanı tanıtıcısının yerel türünü tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d7f0b-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7f0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7f0b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorArgType {  
  
    IMAGE_CEE_CS_END        = 0x0,  
    IMAGE_CEE_CS_VOID       = 0x1,  
    IMAGE_CEE_CS_I4         = 0x2,  
    IMAGE_CEE_CS_I8         = 0x3,  
    IMAGE_CEE_CS_R4         = 0x4,  
    IMAGE_CEE_CS_R8         = 0x5,  
    IMAGE_CEE_CS_PTR        = 0x6,  
    IMAGE_CEE_CS_OBJECT     = 0x7,  
    IMAGE_CEE_CS_STRUCT4    = 0x8,  
    IMAGE_CEE_CS_STRUCT32   = 0x9,  
    IMAGE_CEE_CS_BYVALUE    = 0xA  
  
} CorArgType;  
```  
  
## <a name="requirements"></a><span data-ttu-id="d7f0b-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7f0b-105">Requirements</span></span>  
 <span data-ttu-id="d7f0b-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7f0b-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7f0b-107">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d7f0b-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d7f0b-108">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7f0b-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f0b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7f0b-109">See also</span></span>

- [<span data-ttu-id="d7f0b-110">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d7f0b-110">Metadata Enumerations</span></span>](metadata-enumerations.md)

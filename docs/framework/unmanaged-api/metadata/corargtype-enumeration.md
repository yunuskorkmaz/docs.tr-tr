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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af9ca932a4c4a12a2c89571f40162a4ecbd5c33d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144501"
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="ca471-102">CorArgType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ca471-102">CorArgType Enumeration</span></span>
<span data-ttu-id="ca471-103">Yerel bir çalışma zamanı tanıtıcısı türünü açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ca471-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca471-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca471-104">Syntax</span></span>  
  
```  
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
  
## <a name="requirements"></a><span data-ttu-id="ca471-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca471-105">Requirements</span></span>  
 <span data-ttu-id="ca471-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca471-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca471-107">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ca471-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ca471-108">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca471-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca471-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca471-109">See also</span></span>

- [<span data-ttu-id="ca471-110">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ca471-110">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

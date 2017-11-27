---
title: "CorArgType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorArgType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorArgType
helpviewer_keywords: CorArgType enumeration [.NET Framework metadata]
ms.assetid: 3c1cb268-57a0-4664-91c7-f6908ff29e32
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22034b575dee2840cb89b949f5c663df27cefc4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="3b7d8-102">CorArgType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3b7d8-102">CorArgType Enumeration</span></span>
<span data-ttu-id="3b7d8-103">Bir çalışma zamanı tanıtıcı yerel türünü tanımlayan değerler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3b7d8-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b7d8-104">Syntax</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="3b7d8-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b7d8-105">Requirements</span></span>  
 <span data-ttu-id="3b7d8-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b7d8-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b7d8-107">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3b7d8-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3b7d8-108">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b7d8-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7d8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b7d8-109">See Also</span></span>  
 [<span data-ttu-id="3b7d8-110">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="3b7d8-110">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

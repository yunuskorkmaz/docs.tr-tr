---
title: "CorThreadSafetyOptions Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorThreadSafetyOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorThreadSafetyOptions
helpviewer_keywords: CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ccdd7fb2b97e98227a581b3b97783c2c47bcab1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="95837-102">CorThreadSafetyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="95837-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="95837-103">İş parçacığı güvenliği seçeneklerini seçmek için bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="95837-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95837-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95837-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="95837-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="95837-105">Members</span></span>  
  
|<span data-ttu-id="95837-106">Üye</span><span class="sxs-lookup"><span data-stu-id="95837-106">Member</span></span>|<span data-ttu-id="95837-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95837-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="95837-108">Varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="95837-108">Default value.</span></span> <span data-ttu-id="95837-109">Aynı `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="95837-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="95837-110">Okuyucu/Yazıcı kilit ayarlanamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="95837-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="95837-111">Okuyucu/Yazıcı kilit ayarlanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="95837-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95837-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95837-112">Requirements</span></span>  
 <span data-ttu-id="95837-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95837-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95837-114">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="95837-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="95837-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95837-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95837-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95837-116">See Also</span></span>  
 [<span data-ttu-id="95837-117">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="95837-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

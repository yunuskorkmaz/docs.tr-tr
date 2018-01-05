---
title: "CorNativeLinkFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkFlags
helpviewer_keywords: CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8477ef13c53db6cc4de58c4e707a82e2ab7f650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="2d7e0-102">CorNativeLinkFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2d7e0-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="2d7e0-103">Yerel kod bağlarken bağlayıcı tarafından kullanılan bayrak değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d7e0-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d7e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d7e0-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2d7e0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2d7e0-105">Members</span></span>  
  
|<span data-ttu-id="2d7e0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2d7e0-106">Member</span></span>|<span data-ttu-id="2d7e0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d7e0-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="2d7e0-108">Hiçbir bayrakları gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d7e0-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="2d7e0-109">Gösteren bir `setLastError` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2d7e0-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="2d7e0-110">Gösteren bir `nomangle` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2d7e0-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="2d7e0-111">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="2d7e0-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d7e0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d7e0-112">Requirements</span></span>  
 <span data-ttu-id="2d7e0-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d7e0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d7e0-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d7e0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d7e0-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2d7e0-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d7e0-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d7e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d7e0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d7e0-117">See Also</span></span>  
 [<span data-ttu-id="2d7e0-118">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2d7e0-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

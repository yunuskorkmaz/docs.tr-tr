---
title: "CorRegFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRegFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRegFlags
helpviewer_keywords: CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8118de9f4fc6a4f2820b88685b9b87c498328b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="6f372-102">CorRegFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6f372-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="6f372-103">Kayıt için bir modül veya bileşik görüntü yüklenirken kullanılan bayrak değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f372-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f372-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f372-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6f372-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6f372-105">Members</span></span>  
  
|<span data-ttu-id="6f372-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6f372-106">Member</span></span>|<span data-ttu-id="6f372-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f372-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="6f372-108">Dosyaları hedefe kopyalanmaması gereken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f372-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="6f372-109">Modül veya bileşik bir yapılandırma olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f372-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="6f372-110">Modül veya bileşik sınıf başvurularını olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f372-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f372-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f372-111">Requirements</span></span>  
 <span data-ttu-id="6f372-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f372-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f372-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6f372-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f372-114">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6f372-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f372-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f372-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f372-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f372-116">See Also</span></span>  
 [<span data-ttu-id="6f372-117">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="6f372-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

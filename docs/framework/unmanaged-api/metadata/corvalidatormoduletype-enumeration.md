---
title: "CorValidatorModuleType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorValidatorModuleType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorValidatorModuleType
helpviewer_keywords: CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3367f6928b5d7378b2686185ee3e03d0279cc11d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="e81ce-102">CorValidatorModuleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e81ce-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="e81ce-103">Bir modül türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e81ce-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e81ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e81ce-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="e81ce-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e81ce-105">Members</span></span>  
  
|<span data-ttu-id="e81ce-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e81ce-106">Member</span></span>|<span data-ttu-id="e81ce-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e81ce-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="e81ce-108">Geçersiz bir tür modülüdür.</span><span class="sxs-lookup"><span data-stu-id="e81ce-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="e81ce-109">En küçük değerini `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="e81ce-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="e81ce-110">Modül bir taşınabilir yürütülebilir (PE) dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e81ce-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="e81ce-111">Modül bir .obj dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e81ce-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="e81ce-112">Düzenle ve devam et hata ayıklayıcı oturum modülüdür.</span><span class="sxs-lookup"><span data-stu-id="e81ce-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="e81ce-113">Modül artımlı olarak yerleşik biridir.</span><span class="sxs-lookup"><span data-stu-id="e81ce-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="e81ce-114">En büyük değerini `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="e81ce-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e81ce-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e81ce-115">Requirements</span></span>  
 <span data-ttu-id="e81ce-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e81ce-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e81ce-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e81ce-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e81ce-118">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e81ce-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e81ce-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e81ce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e81ce-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e81ce-120">See Also</span></span>  
 [<span data-ttu-id="e81ce-121">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e81ce-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

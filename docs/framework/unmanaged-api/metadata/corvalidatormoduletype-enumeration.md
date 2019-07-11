---
title: CorValidatorModuleType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04bed418d96658e29328cf2ce6bba445639b437f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750761"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="76d77-102">CorValidatorModuleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="76d77-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="76d77-103">Bir modül türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="76d77-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76d77-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="76d77-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="76d77-105">Members</span></span>  
  
|<span data-ttu-id="76d77-106">Üye</span><span class="sxs-lookup"><span data-stu-id="76d77-106">Member</span></span>|<span data-ttu-id="76d77-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76d77-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="76d77-108">Modül geçersiz bir türdür.</span><span class="sxs-lookup"><span data-stu-id="76d77-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="76d77-109">En küçük değerini `CorValidatorModuleType` sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="76d77-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="76d77-110">Modül bir taşınabilir yürütülebilir (PE) dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="76d77-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="76d77-111">Bir .obj dosyası modülüdür.</span><span class="sxs-lookup"><span data-stu-id="76d77-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="76d77-112">Düzenle ve devam et hata ayıklayıcı oturumu modülüdür.</span><span class="sxs-lookup"><span data-stu-id="76d77-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="76d77-113">Artımlı olarak derlenen bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="76d77-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="76d77-114">En büyük değerini `CorValidatorModuleType` sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="76d77-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76d77-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76d77-115">Requirements</span></span>  
 <span data-ttu-id="76d77-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76d77-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76d77-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="76d77-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76d77-118">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="76d77-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76d77-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76d77-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d77-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76d77-120">See also</span></span>

- [<span data-ttu-id="76d77-121">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="76d77-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

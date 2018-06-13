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
ms.openlocfilehash: 97e9ae5a7c35b4f9b6e2b4ca7e754b5b7480dfa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444146"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="8e498-102">CorValidatorModuleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8e498-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="8e498-103">Bir modül türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e498-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e498-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e498-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8e498-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8e498-105">Members</span></span>  
  
|<span data-ttu-id="8e498-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8e498-106">Member</span></span>|<span data-ttu-id="8e498-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e498-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="8e498-108">Geçersiz bir tür modülüdür.</span><span class="sxs-lookup"><span data-stu-id="8e498-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="8e498-109">En küçük değerini `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="8e498-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="8e498-110">Modül bir taşınabilir yürütülebilir (PE) dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e498-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="8e498-111">Modül bir .obj dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e498-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="8e498-112">Düzenle ve devam et hata ayıklayıcı oturum modülüdür.</span><span class="sxs-lookup"><span data-stu-id="8e498-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="8e498-113">Modül artımlı olarak yerleşik biridir.</span><span class="sxs-lookup"><span data-stu-id="8e498-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="8e498-114">En büyük değerini `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="8e498-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e498-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e498-115">Requirements</span></span>  
 <span data-ttu-id="8e498-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e498-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e498-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8e498-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e498-118">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8e498-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e498-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e498-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e498-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e498-120">See Also</span></span>  
 [<span data-ttu-id="8e498-121">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8e498-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

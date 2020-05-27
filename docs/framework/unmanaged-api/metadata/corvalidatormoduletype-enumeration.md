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
ms.openlocfilehash: 038e2ec20e5fd01edf9835080e0f7a15ec862fd9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008943"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="c2848-102">CorValidatorModuleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c2848-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="c2848-103">Modülün türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2848-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2848-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2848-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c2848-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c2848-105">Members</span></span>  
  
|<span data-ttu-id="c2848-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c2848-106">Member</span></span>|<span data-ttu-id="c2848-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2848-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="c2848-108">Modül geçersiz bir tür.</span><span class="sxs-lookup"><span data-stu-id="c2848-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="c2848-109">Sabit listesinin en küçük değeri `CorValidatorModuleType` .</span><span class="sxs-lookup"><span data-stu-id="c2848-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="c2848-110">Modül, taşınabilir bir çalıştırılabilir (PE) dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c2848-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="c2848-111">Modül bir. obj dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c2848-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="c2848-112">Modül, Düzenle ve devam et hata ayıklayıcı oturumundur.</span><span class="sxs-lookup"><span data-stu-id="c2848-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="c2848-113">Modül artımlı olarak oluşturulan bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="c2848-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="c2848-114">Sabit listesinin en büyük değeri `CorValidatorModuleType` .</span><span class="sxs-lookup"><span data-stu-id="c2848-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2848-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2848-115">Requirements</span></span>  
 <span data-ttu-id="c2848-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2848-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2848-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c2848-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2848-118">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c2848-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2848-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2848-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2848-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2848-120">See also</span></span>

- [<span data-ttu-id="c2848-121">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="c2848-121">Metadata Enumerations</span></span>](metadata-enumerations.md)

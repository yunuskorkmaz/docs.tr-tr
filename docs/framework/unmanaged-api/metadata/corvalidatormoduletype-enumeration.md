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
ms.openlocfilehash: 2fb7f11677870f7d53439f1867f167fabe70b22a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723863"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="4b279-102">CorValidatorModuleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4b279-102">CorValidatorModuleType Enumeration</span></span>

<span data-ttu-id="4b279-103">Modülün türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b279-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b279-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b279-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4b279-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4b279-105">Members</span></span>  
  
|<span data-ttu-id="4b279-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4b279-106">Member</span></span>|<span data-ttu-id="4b279-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b279-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="4b279-108">Modül geçersiz bir tür.</span><span class="sxs-lookup"><span data-stu-id="4b279-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="4b279-109">Sabit listesinin en küçük değeri `CorValidatorModuleType` .</span><span class="sxs-lookup"><span data-stu-id="4b279-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="4b279-110">Modül, taşınabilir bir çalıştırılabilir (PE) dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="4b279-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="4b279-111">Modül bir. obj dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="4b279-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="4b279-112">Modül, Düzenle ve devam et hata ayıklayıcı oturumundur.</span><span class="sxs-lookup"><span data-stu-id="4b279-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="4b279-113">Modül artımlı olarak oluşturulan bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="4b279-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="4b279-114">Sabit listesinin en büyük değeri `CorValidatorModuleType` .</span><span class="sxs-lookup"><span data-stu-id="4b279-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b279-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b279-115">Requirements</span></span>  

 <span data-ttu-id="4b279-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b279-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b279-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4b279-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b279-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4b279-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b279-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b279-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b279-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b279-120">See also</span></span>

- [<span data-ttu-id="4b279-121">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="4b279-121">Metadata Enumerations</span></span>](metadata-enumerations.md)

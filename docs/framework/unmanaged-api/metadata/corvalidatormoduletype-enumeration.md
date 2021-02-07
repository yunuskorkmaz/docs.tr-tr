---
description: 'Daha fazla bilgi edinin: CorValidatorModuleType numaralandırması'
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
ms.openlocfilehash: 13792c461660ddd8cfd530f5b34d642d806cdea4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707273"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="6678b-103">CorValidatorModuleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6678b-103">CorValidatorModuleType Enumeration</span></span>

<span data-ttu-id="6678b-104">Modülün türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6678b-104">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6678b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6678b-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6678b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6678b-106">Members</span></span>  
  
|<span data-ttu-id="6678b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="6678b-107">Member</span></span>|<span data-ttu-id="6678b-108">Description</span><span class="sxs-lookup"><span data-stu-id="6678b-108">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="6678b-109">Modül geçersiz bir tür.</span><span class="sxs-lookup"><span data-stu-id="6678b-109">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="6678b-110">Sabit listesinin en küçük değeri `CorValidatorModuleType` .</span><span class="sxs-lookup"><span data-stu-id="6678b-110">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="6678b-111">Modül, taşınabilir bir çalıştırılabilir (PE) dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="6678b-111">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="6678b-112">Modül bir. obj dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="6678b-112">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="6678b-113">Modül, Düzenle ve devam et hata ayıklayıcı oturumundur.</span><span class="sxs-lookup"><span data-stu-id="6678b-113">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="6678b-114">Modül artımlı olarak oluşturulan bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="6678b-114">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="6678b-115">Sabit listesinin en büyük değeri `CorValidatorModuleType` .</span><span class="sxs-lookup"><span data-stu-id="6678b-115">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6678b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6678b-116">Requirements</span></span>  

 <span data-ttu-id="6678b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6678b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6678b-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6678b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6678b-119">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6678b-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6678b-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6678b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6678b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6678b-121">See also</span></span>

- [<span data-ttu-id="6678b-122">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="6678b-122">Metadata Enumerations</span></span>](metadata-enumerations.md)

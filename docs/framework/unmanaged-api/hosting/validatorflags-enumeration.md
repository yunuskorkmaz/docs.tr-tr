---
title: ValidatorFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e982fa7f6354f341ff4718440f345e282a1d20d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492228"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="4ab81-102">ValidatorFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4ab81-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="4ab81-103">Bir çağrıda gerçekleştirilmelidir doğrulama türünü gösteren değerleri içerir [Iclrvalidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ab81-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ab81-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="4ab81-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4ab81-105">Members</span></span>  
  
|<span data-ttu-id="4ab81-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4ab81-106">Member</span></span>|<span data-ttu-id="4ab81-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ab81-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="4ab81-108">Yalnızca Microsoft Ara dilini (MSIL) yürütülebilir dosyasına doğrulanmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ab81-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="4ab81-109">Sadece yürütülebilir dosya biçimi doğrulanmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ab81-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="4ab81-110">Tüm doğrulama türlerinin gerçekleştirilen ve üzerinde bildirilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ab81-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="4ab81-111">Yürütülebilir dosya biçiminin geçerliliğinin doğrulanması belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ab81-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="4ab81-112">Doğrulama hatası iletilerinin doğrulama hatalarını yükseltmek kaynak kodu satırlarını içermesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ab81-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="4ab81-113">Bu alanın değeri, .NET Framework 2.0 sürümünde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="4ab81-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ab81-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ab81-114">Requirements</span></span>  
 <span data-ttu-id="4ab81-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ab81-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab81-116">**Üst bilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="4ab81-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="4ab81-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ab81-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ab81-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab81-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab81-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ab81-119">See also</span></span>
- [<span data-ttu-id="4ab81-120">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ab81-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="4ab81-121">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4ab81-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

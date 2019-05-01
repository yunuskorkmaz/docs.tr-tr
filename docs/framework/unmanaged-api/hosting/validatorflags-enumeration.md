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
ms.openlocfilehash: fa10ae1cf67339a6719210f3162f19ac648e8ee5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942356"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="6bc0b-102">ValidatorFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6bc0b-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="6bc0b-103">Bir çağrıda gerçekleştirilmelidir doğrulama türünü gösteren değerleri içerir [Iclrvalidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6bc0b-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bc0b-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="6bc0b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6bc0b-105">Members</span></span>  
  
|<span data-ttu-id="6bc0b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6bc0b-106">Member</span></span>|<span data-ttu-id="6bc0b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bc0b-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="6bc0b-108">Yalnızca Microsoft Ara dilini (MSIL) yürütülebilir dosyasına doğrulanmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bc0b-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="6bc0b-109">Sadece yürütülebilir dosya biçimi doğrulanmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bc0b-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="6bc0b-110">Tüm doğrulama türlerinin gerçekleştirilen ve üzerinde bildirilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bc0b-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="6bc0b-111">Yürütülebilir dosya biçiminin geçerliliğinin doğrulanması belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bc0b-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="6bc0b-112">Doğrulama hatası iletilerinin doğrulama hatalarını yükseltmek kaynak kodu satırlarını içermesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bc0b-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="6bc0b-113">Bu alanın değeri, .NET Framework 2.0 sürümünde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6bc0b-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bc0b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bc0b-114">Requirements</span></span>  
 <span data-ttu-id="6bc0b-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bc0b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bc0b-116">**Üst bilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="6bc0b-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="6bc0b-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6bc0b-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bc0b-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bc0b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc0b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bc0b-119">See also</span></span>

- [<span data-ttu-id="6bc0b-120">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bc0b-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="6bc0b-121">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6bc0b-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

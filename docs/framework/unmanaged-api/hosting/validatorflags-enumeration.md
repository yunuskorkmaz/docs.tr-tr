---
title: "ValidatorFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ValidatorFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ValidatorFlags
helpviewer_keywords: ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f283beb79ec47454185800bd772904c3c696c7c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="137f9-102">ValidatorFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="137f9-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="137f9-103">Çağrıda gerçekleştirilmelidir doğrulama türünü belirtmek değerleri içeren [Iclrvalidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="137f9-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="137f9-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="137f9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="137f9-105">Members</span></span>  
  
|<span data-ttu-id="137f9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="137f9-106">Member</span></span>|<span data-ttu-id="137f9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="137f9-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="137f9-108">Yalnızca Microsoft Ara dilde (MSIL) yürütülebilir dosyası doğrulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="137f9-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="137f9-109">Yalnızca yürütülebilir dosyasının biçimi doğrulanmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="137f9-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="137f9-110">Her türlü doğrulama gerçekleştirilen ve bildirilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="137f9-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="137f9-111">Yürütülebilir dosya biçimi doğrulanmazsa belirtir.</span><span class="sxs-lookup"><span data-stu-id="137f9-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="137f9-112">Doğrulama hatası iletilerinin doğrulama hataları Yükselt kaynak kod satırlarını içermelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="137f9-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="137f9-113">Bu alanın değeri .NET Framework 2.0 sürümünde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="137f9-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="137f9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="137f9-114">Requirements</span></span>  
 <span data-ttu-id="137f9-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="137f9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="137f9-116">**Başlık:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="137f9-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="137f9-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="137f9-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="137f9-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="137f9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137f9-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="137f9-119">See Also</span></span>  
 [<span data-ttu-id="137f9-120">Iclrerrorreportingmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="137f9-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="137f9-121">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="137f9-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

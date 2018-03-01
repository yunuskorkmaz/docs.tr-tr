---
title: IValidator Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1afa255fa0b1baec35dbd8aa6e0beef62d240c31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidator-interface"></a><span data-ttu-id="e2d5c-102">IValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2d5c-102">IValidator Interface</span></span>
<span data-ttu-id="e2d5c-103">Taşınabilir yürütülebilir (PE) görüntüler doğrulama ve doğrulama hatalarını raporlama için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2d5c-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2d5c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e2d5c-104">Methods</span></span>  
  
|<span data-ttu-id="e2d5c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e2d5c-105">Method</span></span>|<span data-ttu-id="e2d5c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2d5c-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e2d5c-107">Doğrula</span><span class="sxs-lookup"><span data-stu-id="e2d5c-107">Validate</span></span>|<span data-ttu-id="e2d5c-108">Belirtilen PE veya Microsoft Ara dili (MSIL) dosya doğrular.</span><span class="sxs-lookup"><span data-stu-id="e2d5c-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="e2d5c-109">Formateventınfo</span><span class="sxs-lookup"><span data-stu-id="e2d5c-109">FormatEventInfo</span></span>|<span data-ttu-id="e2d5c-110">Belirtilen doğrulama hatası karşılık gelen hata iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="e2d5c-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2d5c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2d5c-111">Requirements</span></span>  
 <span data-ttu-id="e2d5c-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2d5c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2d5c-113">**Başlık:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="e2d5c-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e2d5c-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e2d5c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2d5c-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2d5c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d5c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2d5c-116">See Also</span></span>  
 [<span data-ttu-id="e2d5c-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e2d5c-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="e2d5c-118">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="e2d5c-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)

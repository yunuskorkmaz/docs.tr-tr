---
title: CLRRuntimeHost Coclass’ı
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59fed7519402b4c3c1b2405ea99f8ba484781e95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430749"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="07729-102">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="07729-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="07729-103">Kod yürütmeyi çalışma zamanı tarafından yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="07729-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07729-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07729-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="07729-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="07729-105">Interfaces</span></span>  
  
|<span data-ttu-id="07729-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="07729-106">Interface</span></span>|<span data-ttu-id="07729-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07729-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="07729-108">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07729-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="07729-109">Çalışma zamanı tarafından uygulamaların yürütülmesini denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="07729-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="07729-110">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07729-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="07729-111">Taşınabilir yürütülebilir görüntüler doğrulanması ve ayrıntılı doğrulama hatalarını raporlama için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="07729-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07729-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07729-112">Requirements</span></span>  
 <span data-ttu-id="07729-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07729-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07729-114">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="07729-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="07729-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="07729-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07729-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07729-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07729-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07729-117">See Also</span></span>  
 [<span data-ttu-id="07729-118">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="07729-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)

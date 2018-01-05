---
title: "CLRRuntimeHost Coclass’ı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CLRRuntimeHost
helpviewer_keywords: CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 18e4518a2e321609a8add06c399ed9588748d1ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="b2eea-102">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="b2eea-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="b2eea-103">Kod yürütmeyi çalışma zamanı tarafından yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2eea-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2eea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2eea-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="b2eea-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b2eea-105">Interfaces</span></span>  
  
|<span data-ttu-id="b2eea-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="b2eea-106">Interface</span></span>|<span data-ttu-id="b2eea-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2eea-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="b2eea-108">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2eea-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="b2eea-109">Çalışma zamanı tarafından uygulamaların yürütülmesini denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2eea-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="b2eea-110">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2eea-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="b2eea-111">Taşınabilir yürütülebilir görüntüler doğrulanması ve ayrıntılı doğrulama hatalarını raporlama için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2eea-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2eea-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2eea-112">Requirements</span></span>  
 <span data-ttu-id="b2eea-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2eea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2eea-114">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="b2eea-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="b2eea-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b2eea-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2eea-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2eea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2eea-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2eea-117">See Also</span></span>  
 [<span data-ttu-id="b2eea-118">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="b2eea-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)

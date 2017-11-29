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
ms.openlocfilehash: 372b2466baaa76ba47a6710447d93f9fa6bb967f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="343aa-102">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="343aa-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="343aa-103">Kod yürütmeyi çalışma zamanı tarafından yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="343aa-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="343aa-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="343aa-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="343aa-105">Interfaces</span></span>  
  
|<span data-ttu-id="343aa-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="343aa-106">Interface</span></span>|<span data-ttu-id="343aa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="343aa-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="343aa-108">Iclrruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="343aa-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="343aa-109">Çalışma zamanı tarafından uygulamaların yürütülmesini denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="343aa-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="343aa-110">Iclrvalidator arabirimi</span><span class="sxs-lookup"><span data-stu-id="343aa-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="343aa-111">Taşınabilir yürütülebilir görüntüler doğrulanması ve ayrıntılı doğrulama hatalarını raporlama için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="343aa-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="343aa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="343aa-112">Requirements</span></span>  
 <span data-ttu-id="343aa-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="343aa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="343aa-114">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="343aa-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="343aa-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="343aa-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="343aa-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="343aa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343aa-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="343aa-117">See Also</span></span>  
 [<span data-ttu-id="343aa-118">Barındırma coclass'ları</span><span class="sxs-lookup"><span data-stu-id="343aa-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)

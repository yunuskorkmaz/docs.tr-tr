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
ms.openlocfilehash: 6e40f08a3dae6f17617e97e07a23b9d7eb611083
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558637"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="40ffd-102">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="40ffd-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="40ffd-103">Kod yürütme çalışma zamanı tarafından yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="40ffd-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ffd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40ffd-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="40ffd-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="40ffd-105">Interfaces</span></span>  
  
|<span data-ttu-id="40ffd-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="40ffd-106">Interface</span></span>|<span data-ttu-id="40ffd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40ffd-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="40ffd-108">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40ffd-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="40ffd-109">Çalışma zamanı tarafından uygulamaların yürütülmesini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="40ffd-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="40ffd-110">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40ffd-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="40ffd-111">Doğrulama hatalarını ayrıntılı raporlama için ve doğrulama taşınabilir yürütülebilir görüntü için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="40ffd-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40ffd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40ffd-112">Requirements</span></span>  
 <span data-ttu-id="40ffd-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ffd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ffd-114">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="40ffd-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="40ffd-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="40ffd-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40ffd-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40ffd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ffd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40ffd-117">See also</span></span>
- [<span data-ttu-id="40ffd-118">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="40ffd-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)

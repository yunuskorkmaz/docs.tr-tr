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
ms.openlocfilehash: b1e595e1a4f1b462437f47207b998829a8bd774d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129463"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="9b575-102">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="9b575-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="9b575-103">Çalışma zamanı tarafından kod yürütmeyi yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b575-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b575-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b575-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="9b575-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="9b575-105">Interfaces</span></span>  
  
|<span data-ttu-id="9b575-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="9b575-106">Interface</span></span>|<span data-ttu-id="9b575-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b575-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="9b575-108">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b575-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="9b575-109">Çalışma zamanı tarafından uygulamaların yürütülmesini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b575-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="9b575-110">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b575-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="9b575-111">Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b575-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b575-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b575-112">Requirements</span></span>  
 <span data-ttu-id="9b575-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b575-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b575-114">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="9b575-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="9b575-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9b575-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b575-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b575-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b575-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b575-117">See also</span></span>

- [<span data-ttu-id="9b575-118">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="9b575-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)

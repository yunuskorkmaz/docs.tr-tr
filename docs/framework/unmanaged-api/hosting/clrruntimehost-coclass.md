---
description: 'Daha fazla bilgi edinin: CLRRuntimeHost coclass'
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
ms.openlocfilehash: a371b9b7263f8bb58b5c513de6647320f000beed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799895"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="7818b-103">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="7818b-103">CLRRuntimeHost Coclass</span></span>

<span data-ttu-id="7818b-104">Çalışma zamanı tarafından kod yürütmeyi yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7818b-104">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7818b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7818b-105">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="7818b-106">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="7818b-106">Interfaces</span></span>  
  
|<span data-ttu-id="7818b-107">Arabirim</span><span class="sxs-lookup"><span data-stu-id="7818b-107">Interface</span></span>|<span data-ttu-id="7818b-108">Description</span><span class="sxs-lookup"><span data-stu-id="7818b-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="7818b-109">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7818b-109">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="7818b-110">Çalışma zamanı tarafından uygulamaların yürütülmesini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7818b-110">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="7818b-111">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7818b-111">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="7818b-112">Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7818b-112">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7818b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7818b-113">Requirements</span></span>  

 <span data-ttu-id="7818b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7818b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7818b-115">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="7818b-115">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7818b-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7818b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7818b-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7818b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7818b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7818b-118">See also</span></span>

- [<span data-ttu-id="7818b-119">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="7818b-119">Hosting Coclasses</span></span>](hosting-coclasses.md)

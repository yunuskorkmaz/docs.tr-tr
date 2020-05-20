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
ms.openlocfilehash: 40766ce5837053493f2e3f1f25fe7d1d63ec695f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616811"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="6479e-102">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="6479e-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="6479e-103">Çalışma zamanı tarafından kod yürütmeyi yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6479e-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6479e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6479e-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="6479e-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6479e-105">Interfaces</span></span>  
  
|<span data-ttu-id="6479e-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="6479e-106">Interface</span></span>|<span data-ttu-id="6479e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6479e-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="6479e-108">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6479e-108">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="6479e-109">Çalışma zamanı tarafından uygulamaların yürütülmesini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6479e-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="6479e-110">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6479e-110">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="6479e-111">Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6479e-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6479e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6479e-112">Requirements</span></span>  
 <span data-ttu-id="6479e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6479e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6479e-114">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="6479e-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6479e-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6479e-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6479e-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6479e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6479e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6479e-117">See also</span></span>

- [<span data-ttu-id="6479e-118">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="6479e-118">Hosting Coclasses</span></span>](hosting-coclasses.md)

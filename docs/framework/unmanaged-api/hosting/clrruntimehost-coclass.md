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
ms.openlocfilehash: 7c77cb2e89cb8fd87bf219780b9460649de19c9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731777"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="cb235-102">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="cb235-102">CLRRuntimeHost Coclass</span></span>

<span data-ttu-id="cb235-103">Çalışma zamanı tarafından kod yürütmeyi yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb235-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb235-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb235-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="cb235-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="cb235-105">Interfaces</span></span>  
  
|<span data-ttu-id="cb235-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="cb235-106">Interface</span></span>|<span data-ttu-id="cb235-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb235-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="cb235-108">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb235-108">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="cb235-109">Çalışma zamanı tarafından uygulamaların yürütülmesini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb235-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="cb235-110">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb235-110">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="cb235-111">Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb235-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb235-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb235-112">Requirements</span></span>  

 <span data-ttu-id="cb235-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb235-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb235-114">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="cb235-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="cb235-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cb235-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb235-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb235-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb235-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb235-117">See also</span></span>

- [<span data-ttu-id="cb235-118">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="cb235-118">Hosting Coclasses</span></span>](hosting-coclasses.md)

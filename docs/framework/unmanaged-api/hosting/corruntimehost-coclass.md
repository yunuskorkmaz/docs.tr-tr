---
title: CorRuntimeHost Ortak Sınıfı
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2143fc13db1757ac2fa8a9c5a43f104a0c519ca0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218569"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="ec150-102">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="ec150-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="ec150-103">Ortak dil çalışma zamanı tarafından yürütülen uygulamalarını yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec150-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec150-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec150-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="ec150-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ec150-105">Interfaces</span></span>  
  
|<span data-ttu-id="ec150-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="ec150-106">Interface</span></span>|<span data-ttu-id="ec150-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec150-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ec150-108">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec150-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="ec150-109">Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec150-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="ec150-110">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec150-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="ec150-111">Ortak dil çalışma zamanı oluşturma ve uygulama etki alanları, varsayılan etki alanına ve işlemde çalışan tüm etki alanları listelemek için yapılandırma açıkça durdurmak ve başlatmak konak olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec150-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="ec150-112">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec150-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="ec150-113">Hata Ayıklama Hizmetleri durumuyla ilgili bilgileri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec150-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="ec150-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec150-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="ec150-115">Çöp toplama işleminin bazı yönlerini denetleme ve çöp toplama sistemi hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec150-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="ec150-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="ec150-116">"IValidator"</span></span>|<span data-ttu-id="ec150-117">Taşınabilir yürütülebilir görüntü doğrulama ve ayrıntılı doğrulama hatalarını raporlama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec150-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec150-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec150-118">Requirements</span></span>  
 <span data-ttu-id="ec150-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec150-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec150-120">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="ec150-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="ec150-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ec150-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec150-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec150-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec150-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec150-123">See also</span></span>

- [<span data-ttu-id="ec150-124">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="ec150-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)

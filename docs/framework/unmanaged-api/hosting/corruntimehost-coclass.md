---
title: "CorRuntimeHost Coclass’ı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRuntimeHost
helpviewer_keywords: CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3d7a272aff3a3c7d32042b76d37fdb15c9dcad4d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="6380d-102">CorRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="6380d-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="6380d-103">Ortak dil çalışma zamanı tarafından yürütülen uygulamaları yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6380d-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6380d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6380d-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="6380d-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6380d-105">Interfaces</span></span>  
  
|<span data-ttu-id="6380d-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="6380d-106">Interface</span></span>|<span data-ttu-id="6380d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6380d-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="6380d-108">Icorconfiguration arabirimi</span><span class="sxs-lookup"><span data-stu-id="6380d-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="6380d-109">Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6380d-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="6380d-110">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="6380d-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="6380d-111">Ortak dil çalışma zamanı oluşturmak ve uygulama etki alanları, varsayılan etki alanı erişmek ve tüm etki alanları işlemde çalışan listeleme için yapılandırmak için açıkça durdurmak ve başlatmak ana bilgisayar sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6380d-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="6380d-112">Idebuggerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="6380d-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="6380d-113">Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6380d-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="6380d-114">Igchost arabirimi</span><span class="sxs-lookup"><span data-stu-id="6380d-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="6380d-115">Çöp toplama sistemi hakkında bilgi edinme ve atık toplama bazı yönlerini denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6380d-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="6380d-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="6380d-116">"IValidator"</span></span>|<span data-ttu-id="6380d-117">Taşınabilir yürütülebilir görüntüler doğrulanması ve ayrıntılı doğrulama hatalarını raporlama için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6380d-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6380d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6380d-118">Requirements</span></span>  
 <span data-ttu-id="6380d-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6380d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6380d-120">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="6380d-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6380d-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6380d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6380d-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6380d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6380d-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6380d-123">See Also</span></span>  
 [<span data-ttu-id="6380d-124">Barındırma coclass'ları</span><span class="sxs-lookup"><span data-stu-id="6380d-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)

---
title: ICLRControl Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl
helpviewer_keywords: ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98b41ea0062534d9e990a7fe366e8f746ae87f38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="48787-102">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-102">ICLRControl Interface</span></span>
<span data-ttu-id="48787-103">Başvurular almak konak izin vermek ve yönlerini, ortak dil çalışma zamanı (CLR) yapılandırma yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="48787-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48787-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="48787-104">Methods</span></span>  
  
|<span data-ttu-id="48787-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="48787-105">Method</span></span>|<span data-ttu-id="48787-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48787-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48787-107">GetCLRManager yöntemi</span><span class="sxs-lookup"><span data-stu-id="48787-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="48787-108">Arabirim işaretçisi herhangi bir ana bilgisayar CLR yapılandırmak için kullanabileceğiniz Yöneticisi türü örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="48787-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="48787-109">SetAppDomainManagerType yöntemi</span><span class="sxs-lookup"><span data-stu-id="48787-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="48787-110">Öğesinden türetilen bir tür ayarlar <xref:System.AppDomainManager> uygulama etki alanı yöneticileri için türü olarak.</span><span class="sxs-lookup"><span data-stu-id="48787-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="48787-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48787-111">Requirements</span></span>  
 <span data-ttu-id="48787-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48787-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48787-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48787-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48787-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="48787-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48787-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48787-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48787-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48787-116">See Also</span></span>  
 [<span data-ttu-id="48787-117">Iclrassemblyıdentitymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="48787-118">Iclrdebugmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="48787-119">Iclrgcmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="48787-120">Iclrhostbindingpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="48787-121">Iclrhostprotectionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="48787-122">Iclroneventmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="48787-123">Iclrpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="48787-124">Ihostcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="48787-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="48787-125">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="48787-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

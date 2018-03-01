---
title: ICLRControl Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b93d87107e1a69b0a047dbf156124fe49cd95d16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="1b3fe-102">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-102">ICLRControl Interface</span></span>
<span data-ttu-id="1b3fe-103">Başvurular almak konak izin vermek ve yönlerini, ortak dil çalışma zamanı (CLR) yapılandırma yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b3fe-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b3fe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1b3fe-104">Methods</span></span>  
  
|<span data-ttu-id="1b3fe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1b3fe-105">Method</span></span>|<span data-ttu-id="1b3fe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b3fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b3fe-107">GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="1b3fe-108">Arabirim işaretçisi herhangi bir ana bilgisayar CLR yapılandırmak için kullanabileceğiniz Yöneticisi türü örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="1b3fe-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="1b3fe-109">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="1b3fe-110">Öğesinden türetilen bir tür ayarlar <xref:System.AppDomainManager> uygulama etki alanı yöneticileri için türü olarak.</span><span class="sxs-lookup"><span data-stu-id="1b3fe-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b3fe-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b3fe-111">Requirements</span></span>  
 <span data-ttu-id="1b3fe-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b3fe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b3fe-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b3fe-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b3fe-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1b3fe-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b3fe-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b3fe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b3fe-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b3fe-116">See Also</span></span>  
 [<span data-ttu-id="1b3fe-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="1b3fe-118">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="1b3fe-119">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="1b3fe-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="1b3fe-121">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="1b3fe-122">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="1b3fe-123">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="1b3fe-124">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3fe-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="1b3fe-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b3fe-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

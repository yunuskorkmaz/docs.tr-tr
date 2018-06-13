---
title: ICLRControl Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a06c1f4e1fcfe9c9c361a0e0bb2e8722577a13b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432901"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="ecd46-102">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-102">ICLRControl Interface</span></span>
<span data-ttu-id="ecd46-103">Başvurular almak konak izin vermek ve yönlerini, ortak dil çalışma zamanı (CLR) yapılandırma yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecd46-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecd46-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ecd46-104">Methods</span></span>  
  
|<span data-ttu-id="ecd46-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ecd46-105">Method</span></span>|<span data-ttu-id="ecd46-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecd46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecd46-107">GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd46-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="ecd46-108">Arabirim işaretçisi herhangi bir ana bilgisayar CLR yapılandırmak için kullanabileceğiniz Yöneticisi türü örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="ecd46-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="ecd46-109">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd46-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="ecd46-110">Öğesinden türetilen bir tür ayarlar <xref:System.AppDomainManager> uygulama etki alanı yöneticileri için türü olarak.</span><span class="sxs-lookup"><span data-stu-id="ecd46-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecd46-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecd46-111">Requirements</span></span>  
 <span data-ttu-id="ecd46-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd46-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd46-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ecd46-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecd46-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ecd46-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecd46-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd46-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd46-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecd46-116">See Also</span></span>  
 [<span data-ttu-id="ecd46-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ecd46-118">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="ecd46-119">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="ecd46-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="ecd46-121">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="ecd46-122">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="ecd46-123">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="ecd46-124">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd46-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="ecd46-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ecd46-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

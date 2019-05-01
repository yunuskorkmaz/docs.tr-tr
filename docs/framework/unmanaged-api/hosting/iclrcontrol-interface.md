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
ms.openlocfilehash: f70e7958cc9ac198738ed72732fe7b6563c89067
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970072"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="85d37-102">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-102">ICLRControl Interface</span></span>
<span data-ttu-id="85d37-103">Başvuru almak konak izin vermek ve yönlerini, ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="85d37-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85d37-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="85d37-104">Methods</span></span>  
  
|<span data-ttu-id="85d37-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="85d37-105">Method</span></span>|<span data-ttu-id="85d37-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85d37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85d37-107">GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85d37-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="85d37-108">CLR yapılandırmak için konak kullanabilirsiniz manager türlerinden herhangi birinin bir örneği için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="85d37-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="85d37-109">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85d37-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="85d37-110">Türetilen bir türü ayarlar <xref:System.AppDomainManager> uygulama etki alanı yöneticileri için türü.</span><span class="sxs-lookup"><span data-stu-id="85d37-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85d37-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85d37-111">Requirements</span></span>  
 <span data-ttu-id="85d37-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d37-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d37-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="85d37-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85d37-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="85d37-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85d37-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85d37-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d37-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85d37-116">See also</span></span>

- [<span data-ttu-id="85d37-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="85d37-118">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="85d37-119">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="85d37-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="85d37-121">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="85d37-122">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="85d37-123">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="85d37-124">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85d37-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="85d37-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="85d37-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

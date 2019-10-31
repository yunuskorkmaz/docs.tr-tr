---
title: IHostPolicyManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: 6ba7b7adc104db528293d77c3591370c6ce02c25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128595"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="01605-102">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01605-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="01605-103">Ortak dil çalışma zamanının (CLR) iptal, zaman aşımları veya hatalara karşı gerçekleştirdiği eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="01605-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01605-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="01605-104">Methods</span></span>  
  
|<span data-ttu-id="01605-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="01605-105">Method</span></span>|<span data-ttu-id="01605-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01605-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01605-107">OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01605-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="01605-108">Bir iş parçacığı <xref:System.AppDomain> iptaline yanıt olarak bir [ICLRPolicyManager:: SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) çağrısıyla belirtilen varsayılan eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="01605-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="01605-109">OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01605-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="01605-110">Kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="01605-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="01605-111">OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01605-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="01605-112">Bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="01605-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01605-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01605-113">Requirements</span></span>  
 <span data-ttu-id="01605-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01605-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01605-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01605-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01605-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="01605-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01605-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01605-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01605-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01605-118">See also</span></span>

- [<span data-ttu-id="01605-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="01605-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="01605-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="01605-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="01605-121">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="01605-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="01605-122">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01605-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="01605-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="01605-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

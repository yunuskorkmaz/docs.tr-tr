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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9d903b4e44ea7a185ad8b3b71b7a5da2f2bda3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126353"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="620ea-102">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="620ea-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="620ea-103">Ana bilgisayarının durumunda, ortak dil çalışma zamanı (CLR) gerçekleştirdiği işlemleri durdurur, zaman aşımı veya hataları bildirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="620ea-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="620ea-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="620ea-104">Methods</span></span>  
  
|<span data-ttu-id="620ea-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="620ea-105">Method</span></span>|<span data-ttu-id="620ea-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="620ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="620ea-107">OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="620ea-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="620ea-108">Bir çağrı tarafından belirtilen varsayılan eylem gerçekleştirmek üzere CLR, konağa bildirir [Iclrpolicymanager::setdefaultaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) yanıt olarak bir iş parçacığını durdurmak veya <xref:System.AppDomain> kaldırın.</span><span class="sxs-lookup"><span data-stu-id="620ea-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="620ea-109">OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="620ea-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="620ea-110">CLR bir çağrı tarafından belirtilen eylemi gerçekleştirmek için bir konağa bildirir [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yanıt olarak bir kaynak ayırma veya geri kazanma hatası.</span><span class="sxs-lookup"><span data-stu-id="620ea-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="620ea-111">OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="620ea-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="620ea-112">CLR bir çağrı tarafından belirtilen eylemi gerçekleştirmek için bir konağa bildirir [Iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yanıt olarak bir zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="620ea-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="620ea-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="620ea-113">Requirements</span></span>  
 <span data-ttu-id="620ea-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="620ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="620ea-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="620ea-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="620ea-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="620ea-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="620ea-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="620ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620ea-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="620ea-118">See also</span></span>

- [<span data-ttu-id="620ea-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="620ea-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="620ea-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="620ea-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="620ea-121">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="620ea-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="620ea-122">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="620ea-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="620ea-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="620ea-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

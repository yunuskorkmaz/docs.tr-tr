---
title: IHostPolicyManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager
helpviewer_keywords: IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8f49474f1a75af91ac5296be866914e05732e755
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="138c9-102">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="138c9-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="138c9-103">Durumunda, ortak dil çalışma zamanı (CLR) gerçekleştirdiği işlemleri ana durdurur, zaman aşımı veya hatalar bildiren yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="138c9-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="138c9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="138c9-104">Methods</span></span>  
  
|<span data-ttu-id="138c9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="138c9-105">Method</span></span>|<span data-ttu-id="138c9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="138c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="138c9-107">OnDefaultAction yöntemi</span><span class="sxs-lookup"><span data-stu-id="138c9-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="138c9-108">Bir çağrı tarafından belirtilen varsayılan eylem gerçekleştirmek üzere CLR olan konak bildirir [Iclrpolicymanager::setdefaultaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) yanıt olarak bir iş parçacığı iptal etmek veya <xref:System.AppDomain> kaldırın.</span><span class="sxs-lookup"><span data-stu-id="138c9-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="138c9-109">OnFailure yöntemi</span><span class="sxs-lookup"><span data-stu-id="138c9-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="138c9-110">Bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere CLR olan konak bildirir [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yanıt olarak kaynak ayırma veya geri kazanma hatası.</span><span class="sxs-lookup"><span data-stu-id="138c9-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="138c9-111">OnTimeout yöntemi</span><span class="sxs-lookup"><span data-stu-id="138c9-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="138c9-112">Bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere CLR olan konak bildirir [Iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yanıt olarak bir zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="138c9-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="138c9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="138c9-113">Requirements</span></span>  
 <span data-ttu-id="138c9-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="138c9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="138c9-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="138c9-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="138c9-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="138c9-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="138c9-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="138c9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="138c9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="138c9-118">See Also</span></span>  
 [<span data-ttu-id="138c9-119">EClrFailure numaralandırması</span><span class="sxs-lookup"><span data-stu-id="138c9-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="138c9-120">EClrOperation numaralandırması</span><span class="sxs-lookup"><span data-stu-id="138c9-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="138c9-121">EPolicyAction numaralandırması</span><span class="sxs-lookup"><span data-stu-id="138c9-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="138c9-122">Iclrpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="138c9-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="138c9-123">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="138c9-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

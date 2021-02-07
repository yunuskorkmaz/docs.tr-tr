---
description: 'Şu konuda daha fazla bilgi edinin: IHostPolicyManager arabirimi'
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
ms.openlocfilehash: d823ee2526019188afd17df903b61a720e18207f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671938"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="6a390-103">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a390-103">IHostPolicyManager Interface</span></span>

<span data-ttu-id="6a390-104">Ortak dil çalışma zamanının (CLR) iptal, zaman aşımları veya hatalara karşı gerçekleştirdiği eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a390-104">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a390-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6a390-105">Methods</span></span>  
  
|<span data-ttu-id="6a390-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6a390-106">Method</span></span>|<span data-ttu-id="6a390-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a390-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a390-108">OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a390-108">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="6a390-109">Bir iş parçacığının iptal veya kaldırma yanıtı olarak [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) çağrısıyla belirtilen varsayılan eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="6a390-109">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="6a390-110">OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a390-110">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="6a390-111">Kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="6a390-111">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="6a390-112">OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a390-112">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="6a390-113">Bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="6a390-113">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a390-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a390-114">Requirements</span></span>  

 <span data-ttu-id="6a390-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a390-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a390-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6a390-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a390-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6a390-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a390-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a390-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a390-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a390-119">See also</span></span>

- [<span data-ttu-id="6a390-120">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6a390-120">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="6a390-121">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6a390-121">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="6a390-122">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6a390-122">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="6a390-123">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a390-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="6a390-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6a390-124">Hosting Interfaces</span></span>](hosting-interfaces.md)

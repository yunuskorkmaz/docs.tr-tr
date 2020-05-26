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
ms.openlocfilehash: db089a55128fa675ceedf157b046fe205d8c6b51
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804337"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="80238-102">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80238-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="80238-103">Ortak dil çalışma zamanının (CLR) iptal, zaman aşımları veya hatalara karşı gerçekleştirdiği eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="80238-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80238-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="80238-104">Methods</span></span>  
  
|<span data-ttu-id="80238-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="80238-105">Method</span></span>|<span data-ttu-id="80238-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80238-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80238-107">OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80238-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="80238-108">Bir iş parçacığının iptal veya kaldırma yanıtı olarak [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) çağrısıyla belirtilen varsayılan eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="80238-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="80238-109">OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80238-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="80238-110">Kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="80238-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="80238-111">OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80238-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="80238-112">Bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="80238-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80238-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80238-113">Requirements</span></span>  
 <span data-ttu-id="80238-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80238-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80238-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80238-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80238-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="80238-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80238-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80238-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80238-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80238-118">See also</span></span>

- [<span data-ttu-id="80238-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="80238-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="80238-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="80238-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="80238-121">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="80238-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="80238-122">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80238-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="80238-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="80238-123">Hosting Interfaces</span></span>](hosting-interfaces.md)

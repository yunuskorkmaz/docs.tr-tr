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
ms.openlocfilehash: 3c85bcbe8aee453b19217ebd1f48feea113e3bb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731228"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="f8d14-102">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8d14-102">IHostPolicyManager Interface</span></span>

<span data-ttu-id="f8d14-103">Ortak dil çalışma zamanının (CLR) iptal, zaman aşımları veya hatalara karşı gerçekleştirdiği eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8d14-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8d14-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f8d14-104">Methods</span></span>  
  
|<span data-ttu-id="f8d14-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f8d14-105">Method</span></span>|<span data-ttu-id="f8d14-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8d14-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8d14-107">OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8d14-107">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="f8d14-108">Bir iş parçacığının iptal veya kaldırma yanıtı olarak [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) çağrısıyla belirtilen varsayılan eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="f8d14-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="f8d14-109">OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8d14-109">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="f8d14-110">Kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="f8d14-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="f8d14-111">OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8d14-111">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="f8d14-112">Bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="f8d14-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8d14-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8d14-113">Requirements</span></span>  

 <span data-ttu-id="f8d14-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8d14-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d14-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f8d14-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8d14-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f8d14-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8d14-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d14-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d14-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8d14-118">See also</span></span>

- [<span data-ttu-id="f8d14-119">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f8d14-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="f8d14-120">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f8d14-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="f8d14-121">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f8d14-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="f8d14-122">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8d14-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="f8d14-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f8d14-123">Hosting Interfaces</span></span>](hosting-interfaces.md)

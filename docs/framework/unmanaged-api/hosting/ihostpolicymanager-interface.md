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
ms.openlocfilehash: d6b34403a45cc40863d79b59396041e496989045
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503945"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="8821e-102">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8821e-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="8821e-103">Ortak dil çalışma zamanının (CLR) iptal, zaman aşımları veya hatalara karşı gerçekleştirdiği eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8821e-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8821e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8821e-104">Methods</span></span>  
  
|<span data-ttu-id="8821e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8821e-105">Method</span></span>|<span data-ttu-id="8821e-106">Description</span><span class="sxs-lookup"><span data-stu-id="8821e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8821e-107">OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8821e-107">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="8821e-108">Bir iş parçacığının iptal veya kaldırma yanıtı olarak [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) çağrısıyla belirtilen varsayılan eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="8821e-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="8821e-109">OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8821e-109">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="8821e-110">Kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="8821e-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="8821e-111">OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8821e-111">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="8821e-112">Bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="8821e-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8821e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8821e-113">Requirements</span></span>  
 <span data-ttu-id="8821e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8821e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8821e-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8821e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8821e-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8821e-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8821e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8821e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8821e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8821e-118">See also</span></span>

- [<span data-ttu-id="8821e-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8821e-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="8821e-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8821e-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="8821e-121">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8821e-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="8821e-122">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8821e-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="8821e-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8821e-123">Hosting Interfaces</span></span>](hosting-interfaces.md)

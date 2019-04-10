---
title: ICLRPolicyManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eeccc4dfd7a7147fe791444eeeca2bd3a844305
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211055"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="155e7-102">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="155e7-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="155e7-103">Hataları ve zaman aşımları durumunda uygulanacak ilke eylemleri belirtmek konak sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="155e7-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="155e7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="155e7-104">Methods</span></span>  
  
|<span data-ttu-id="155e7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="155e7-105">Method</span></span>|<span data-ttu-id="155e7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="155e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="155e7-107">SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="155e7-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="155e7-108">Belirtilen bir hata oluşursa, ortak dil çalışma zamanı (CLR) gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="155e7-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="155e7-109">SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="155e7-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="155e7-110">Belirtilen işlem zaman aşımına uğradığında CLR gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="155e7-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="155e7-111">SetDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="155e7-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="155e7-112">Belirtilen işlem oluştuğunda CLR gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="155e7-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="155e7-113">SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="155e7-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="155e7-114">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="155e7-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="155e7-115">SetTimeoutAndAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="155e7-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="155e7-116">Belirtilen işlem için bir zaman aşımı değeri ayarlar ve CLR işlemi oluştuğunda gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="155e7-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="155e7-117">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="155e7-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="155e7-118">İşlenmeyen bir özel durum oluştuğunda CLR'nin davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="155e7-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="155e7-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="155e7-119">Requirements</span></span>  
 <span data-ttu-id="155e7-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="155e7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="155e7-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="155e7-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="155e7-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="155e7-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="155e7-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="155e7-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="155e7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="155e7-124">See also</span></span>

- [<span data-ttu-id="155e7-125">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="155e7-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="155e7-126">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="155e7-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="155e7-127">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="155e7-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="155e7-128">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="155e7-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)

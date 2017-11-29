---
title: ICLRPolicyManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager
helpviewer_keywords: ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3dd904184b730a5b0f5b2dfcac4197e708544d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="57734-102">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57734-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="57734-103">İlke hataları ve zaman aşımları durumunda gerçekleştirilecek eylemleri belirtin konağının yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="57734-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57734-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="57734-104">Methods</span></span>  
  
|<span data-ttu-id="57734-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="57734-105">Method</span></span>|<span data-ttu-id="57734-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57734-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57734-107">SetActionOnFailure yöntemi</span><span class="sxs-lookup"><span data-stu-id="57734-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="57734-108">Belirtilen bir hata oluşursa, ortak dil çalışma zamanı (CLR) gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="57734-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="57734-109">SetActionOnTimeout yöntemi</span><span class="sxs-lookup"><span data-stu-id="57734-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="57734-110">Belirtilen işlem zaman aşımına uğradığında CLR gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="57734-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="57734-111">SetDefaultAction yöntemi</span><span class="sxs-lookup"><span data-stu-id="57734-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="57734-112">Belirtilen işlem oluştuğunda CLR gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="57734-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="57734-113">SetTimeout yöntemi</span><span class="sxs-lookup"><span data-stu-id="57734-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="57734-114">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="57734-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="57734-115">SetTimeoutAndAction yöntemi</span><span class="sxs-lookup"><span data-stu-id="57734-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="57734-116">Belirtilen işlem için bir zaman aşımı değeri ayarlar ve işlemi oluştuğunda CLR gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="57734-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="57734-117">SetUnhandledExceptionPolicy yöntemi</span><span class="sxs-lookup"><span data-stu-id="57734-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="57734-118">İşlenmeyen bir özel durum oluştuğunda CLR davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57734-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57734-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57734-119">Requirements</span></span>  
 <span data-ttu-id="57734-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57734-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57734-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57734-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57734-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="57734-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57734-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57734-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57734-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57734-124">See Also</span></span>  
 [<span data-ttu-id="57734-125">EClrFailure numaralandırması</span><span class="sxs-lookup"><span data-stu-id="57734-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="57734-126">EClrOperation numaralandırması</span><span class="sxs-lookup"><span data-stu-id="57734-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="57734-127">EPolicyAction numaralandırması</span><span class="sxs-lookup"><span data-stu-id="57734-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="57734-128">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="57734-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)

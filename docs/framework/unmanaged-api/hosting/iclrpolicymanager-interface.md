---
description: ': ICLRPolicyManager arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8823f1db8b15b327306ff3c592b46c94537f4331
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637397"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="cbe26-103">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbe26-103">ICLRPolicyManager Interface</span></span>

<span data-ttu-id="cbe26-104">Ana bilgisayarın hatalara ve zaman aşımları durumunda gerçekleştirilecek ilke eylemlerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbe26-104">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cbe26-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cbe26-105">Methods</span></span>  
  
|<span data-ttu-id="cbe26-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cbe26-106">Method</span></span>|<span data-ttu-id="cbe26-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbe26-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cbe26-108">SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbe26-108">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="cbe26-109">Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbe26-109">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="cbe26-110">SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbe26-110">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="cbe26-111">Belirtilen işlem zaman aşımına uğrarsa CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbe26-111">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="cbe26-112">SetDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbe26-112">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="cbe26-113">Belirtilen işlem gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbe26-113">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="cbe26-114">SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbe26-114">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="cbe26-115">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cbe26-115">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="cbe26-116">SetTimeoutAndAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbe26-116">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="cbe26-117">Belirtilen işlem için bir zaman aşımı değeri ayarlar ve işlem gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbe26-117">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="cbe26-118">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbe26-118">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="cbe26-119">İşlenmeyen bir özel durum oluştuğunda CLR 'nin davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbe26-119">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cbe26-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbe26-120">Requirements</span></span>  

 <span data-ttu-id="cbe26-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbe26-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbe26-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cbe26-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbe26-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cbe26-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbe26-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbe26-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe26-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbe26-125">See also</span></span>

- [<span data-ttu-id="cbe26-126">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cbe26-126">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="cbe26-127">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cbe26-127">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="cbe26-128">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cbe26-128">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="cbe26-129">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbe26-129">ICLRControl Interface</span></span>](iclrcontrol-interface.md)

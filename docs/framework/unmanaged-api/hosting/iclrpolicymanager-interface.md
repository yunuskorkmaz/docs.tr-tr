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
ms.openlocfilehash: 7092a1c792fee7f6173dcde211b8e807f6ab02a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725592"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="d2555-102">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2555-102">ICLRPolicyManager Interface</span></span>

<span data-ttu-id="d2555-103">Ana bilgisayarın hatalara ve zaman aşımları durumunda gerçekleştirilecek ilke eylemlerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2555-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2555-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d2555-104">Methods</span></span>  
  
|<span data-ttu-id="d2555-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d2555-105">Method</span></span>|<span data-ttu-id="d2555-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2555-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2555-107">SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2555-107">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="d2555-108">Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2555-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="d2555-109">SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2555-109">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="d2555-110">Belirtilen işlem zaman aşımına uğrarsa CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2555-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="d2555-111">SetDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2555-111">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="d2555-112">Belirtilen işlem gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2555-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="d2555-113">SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2555-113">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="d2555-114">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2555-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="d2555-115">SetTimeoutAndAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2555-115">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="d2555-116">Belirtilen işlem için bir zaman aşımı değeri ayarlar ve işlem gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2555-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="d2555-117">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2555-117">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="d2555-118">İşlenmeyen bir özel durum oluştuğunda CLR 'nin davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2555-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2555-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2555-119">Requirements</span></span>  

 <span data-ttu-id="d2555-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2555-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2555-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d2555-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2555-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d2555-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2555-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2555-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2555-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2555-124">See also</span></span>

- [<span data-ttu-id="d2555-125">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d2555-125">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="d2555-126">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d2555-126">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="d2555-127">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d2555-127">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="d2555-128">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2555-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)

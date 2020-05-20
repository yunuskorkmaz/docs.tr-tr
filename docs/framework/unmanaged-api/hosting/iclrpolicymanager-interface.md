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
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703481"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="61043-102">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61043-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="61043-103">Ana bilgisayarın hatalara ve zaman aşımları durumunda gerçekleştirilecek ilke eylemlerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="61043-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61043-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="61043-104">Methods</span></span>  
  
|<span data-ttu-id="61043-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="61043-105">Method</span></span>|<span data-ttu-id="61043-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61043-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61043-107">SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61043-107">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="61043-108">Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="61043-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="61043-109">SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61043-109">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="61043-110">Belirtilen işlem zaman aşımına uğrarsa CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="61043-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="61043-111">SetDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61043-111">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="61043-112">Belirtilen işlem gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="61043-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="61043-113">SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61043-113">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="61043-114">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="61043-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="61043-115">SetTimeoutAndAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61043-115">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="61043-116">Belirtilen işlem için bir zaman aşımı değeri ayarlar ve işlem gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="61043-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="61043-117">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61043-117">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="61043-118">İşlenmeyen bir özel durum oluştuğunda CLR 'nin davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="61043-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61043-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61043-119">Requirements</span></span>  
 <span data-ttu-id="61043-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61043-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61043-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61043-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61043-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="61043-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61043-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61043-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61043-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61043-124">See also</span></span>

- [<span data-ttu-id="61043-125">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="61043-125">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="61043-126">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="61043-126">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="61043-127">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="61043-127">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="61043-128">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61043-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)

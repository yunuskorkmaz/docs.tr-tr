---
description: 'Şu konuda daha fazla bilgi edinin: IHostPolicyManager:: OnDefaultAction yöntemi'
title: IHostPolicyManager::OnDefaultAction Yöntemi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: ea474734f7bc0a5210c5aecf605452909b261a87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671932"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="00064-103">IHostPolicyManager::OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00064-103">IHostPolicyManager::OnDefaultAction Method</span></span>

<span data-ttu-id="00064-104">Ortak dil çalışma zamanının (CLR), bir iş parçacığı iptali veya kaldırma yanıtı olarak [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) yöntemine yapılan bir çağrı tarafından ayarlanan varsayılan eylemi almak üzere olduğunu bildirir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="00064-104">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00064-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00064-105">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00064-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00064-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="00064-107">'ndaki CLR 'nin yanıt verdiğini belirten olay türünü gösteren [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="00064-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="00064-108">'ndaki CLR 'nin olaya yanıt olarak ele aldığı eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="00064-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00064-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="00064-109">Return Value</span></span>  
  
|<span data-ttu-id="00064-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00064-110">HRESULT</span></span>|<span data-ttu-id="00064-111">Description</span><span class="sxs-lookup"><span data-stu-id="00064-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00064-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="00064-112">S_OK</span></span>|<span data-ttu-id="00064-113">`OnDefaultAction` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="00064-113">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="00064-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00064-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00064-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="00064-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="00064-116">yararlanan</span><span class="sxs-lookup"><span data-stu-id="00064-116">successfully</span></span>|  
|<span data-ttu-id="00064-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00064-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00064-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="00064-118">The call timed out.</span></span>|  
|<span data-ttu-id="00064-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00064-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00064-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="00064-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00064-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00064-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00064-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="00064-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="00064-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00064-123">E_FAIL</span></span>|<span data-ttu-id="00064-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="00064-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00064-125">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="00064-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00064-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="00064-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00064-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00064-127">Requirements</span></span>  

 <span data-ttu-id="00064-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00064-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00064-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="00064-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00064-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="00064-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00064-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00064-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00064-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00064-132">See also</span></span>

- [<span data-ttu-id="00064-133">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="00064-133">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="00064-134">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="00064-134">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="00064-135">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00064-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="00064-136">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00064-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)

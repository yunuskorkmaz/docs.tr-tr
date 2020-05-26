---
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
ms.openlocfilehash: e6aa8cb814e509d310c2f5b5524e0fd6727fc43f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804279"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="c0a48-102">IHostPolicyManager::OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0a48-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="c0a48-103">Ortak dil çalışma zamanının (CLR), bir iş parçacığı iptali veya kaldırma yanıtı olarak [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) yöntemine yapılan bir çağrı tarafından ayarlanan varsayılan eylemi almak üzere olduğunu bildirir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="c0a48-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a48-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c0a48-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0a48-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0a48-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="c0a48-106">'ndaki CLR 'nin yanıt verdiğini belirten olay türünü gösteren [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="c0a48-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="c0a48-107">'ndaki CLR 'nin olaya yanıt olarak ele aldığı eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="c0a48-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0a48-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0a48-108">Return Value</span></span>  
  
|<span data-ttu-id="c0a48-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0a48-109">HRESULT</span></span>|<span data-ttu-id="c0a48-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0a48-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0a48-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0a48-111">S_OK</span></span>|<span data-ttu-id="c0a48-112">`OnDefaultAction`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c0a48-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="c0a48-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c0a48-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c0a48-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c0a48-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="c0a48-115">yararlanan</span><span class="sxs-lookup"><span data-stu-id="c0a48-115">successfully</span></span>|  
|<span data-ttu-id="c0a48-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c0a48-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c0a48-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c0a48-117">The call timed out.</span></span>|  
|<span data-ttu-id="c0a48-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c0a48-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c0a48-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c0a48-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c0a48-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c0a48-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c0a48-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c0a48-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c0a48-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c0a48-122">E_FAIL</span></span>|<span data-ttu-id="c0a48-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c0a48-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c0a48-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c0a48-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c0a48-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0a48-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0a48-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0a48-126">Requirements</span></span>  
 <span data-ttu-id="c0a48-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0a48-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0a48-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c0a48-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0a48-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c0a48-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0a48-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0a48-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0a48-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0a48-131">See also</span></span>

- [<span data-ttu-id="c0a48-132">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c0a48-132">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="c0a48-133">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c0a48-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="c0a48-134">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0a48-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="c0a48-135">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0a48-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)

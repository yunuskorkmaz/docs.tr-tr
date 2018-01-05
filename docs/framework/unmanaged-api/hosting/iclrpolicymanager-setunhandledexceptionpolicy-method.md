---
title: "ICLRPolicyManager::SetUnhandledExceptionPolicy Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ad287fedbc06768dd683c254292e0c28760d59a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="bcb14-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcb14-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="bcb14-103">İşlenmeyen bir özel durum oluştuğunda ortak dil çalışma zamanı (CLR) davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bcb14-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bcb14-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcb14-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bcb14-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="bcb14-106">[in] Aşağıdakilerden birini [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) davranışı CLR veya ana bilgisayar tarafından ayarlanıp ayarlanmadığını gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="bcb14-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bcb14-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bcb14-107">Return Value</span></span>  
  
|<span data-ttu-id="bcb14-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bcb14-108">HRESULT</span></span>|<span data-ttu-id="bcb14-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcb14-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bcb14-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bcb14-110">S_OK</span></span>|<span data-ttu-id="bcb14-111">`SetUnhandledExceptionPolicy`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bcb14-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="bcb14-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bcb14-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bcb14-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bcb14-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bcb14-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bcb14-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bcb14-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bcb14-115">The call timed out.</span></span>|  
|<span data-ttu-id="bcb14-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bcb14-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bcb14-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="bcb14-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bcb14-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bcb14-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bcb14-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="bcb14-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bcb14-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bcb14-120">E_FAIL</span></span>|<span data-ttu-id="bcb14-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bcb14-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bcb14-122">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bcb14-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bcb14-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bcb14-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcb14-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bcb14-124">Remarks</span></span>  
 <span data-ttu-id="bcb14-125">Varsayılan olarak, CLR tüm işlenmeyen özel durumlar için son işleyicisidir ve kendi varsayılan işlem kesmeden davranıştır.</span><span class="sxs-lookup"><span data-stu-id="bcb14-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="bcb14-126">Ana bilgisayar ayarlayarak bu davranışı değiştirebilirsiniz `policy` eHostDeterminedPolicy değeri.</span><span class="sxs-lookup"><span data-stu-id="bcb14-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="bcb14-127">Bu değer, önceki sürümleriyle CLR gibi kendi varsayılan davranışı uygulamak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="bcb14-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcb14-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bcb14-128">Requirements</span></span>  
 <span data-ttu-id="bcb14-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcb14-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcb14-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bcb14-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcb14-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bcb14-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcb14-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcb14-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb14-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bcb14-133">See Also</span></span>  
 [<span data-ttu-id="bcb14-134">EClrUnhandledException Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="bcb14-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 [<span data-ttu-id="bcb14-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcb14-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="bcb14-136">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcb14-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="bcb14-137">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcb14-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)

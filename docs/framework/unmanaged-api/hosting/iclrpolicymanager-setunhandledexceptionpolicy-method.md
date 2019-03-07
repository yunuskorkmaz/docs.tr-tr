---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 734bd51131ea922f00362e7306d34e5241231c13
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466849"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="1502f-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1502f-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="1502f-103">İşlenmeyen bir özel durum oluştuğunda, ortak dil çalışma zamanı (CLR) davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1502f-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1502f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1502f-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1502f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1502f-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="1502f-106">[in] Aşağıdakilerden birini [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) davranışı CLR veya ana bilgisayar tarafından ayarlanıp ayarlanmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1502f-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1502f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1502f-107">Return Value</span></span>  
  
|<span data-ttu-id="1502f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1502f-108">HRESULT</span></span>|<span data-ttu-id="1502f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1502f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1502f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1502f-110">S_OK</span></span>|<span data-ttu-id="1502f-111">`SetUnhandledExceptionPolicy` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1502f-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="1502f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1502f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1502f-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1502f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1502f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1502f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1502f-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1502f-115">The call timed out.</span></span>|  
|<span data-ttu-id="1502f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1502f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1502f-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="1502f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1502f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1502f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1502f-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="1502f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1502f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1502f-120">E_FAIL</span></span>|<span data-ttu-id="1502f-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1502f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1502f-122">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1502f-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1502f-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1502f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1502f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1502f-124">Remarks</span></span>  
 <span data-ttu-id="1502f-125">Varsayılan olarak CLR tüm işlenmemiş özel durumlar için son işleyicisidir ve varsayılan davranışını ayırma işlemi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1502f-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="1502f-126">Konak ayarlayarak bu davranışı değiştirebilirsiniz `policy` eHostDeterminedPolicy değeri.</span><span class="sxs-lookup"><span data-stu-id="1502f-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="1502f-127">Bu değer, önceki sürümleriyle CLR gibi kendi varsayılan davranışı uygulamak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="1502f-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1502f-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1502f-128">Requirements</span></span>  
 <span data-ttu-id="1502f-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1502f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1502f-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1502f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1502f-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1502f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1502f-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1502f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1502f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1502f-133">See also</span></span>
- [<span data-ttu-id="1502f-134">EClrUnhandledException Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1502f-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="1502f-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1502f-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="1502f-136">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1502f-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="1502f-137">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1502f-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)

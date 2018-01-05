---
title: IHostSecurityManager::GetSecurityContext Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.GetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a5fcdf0d0244694a52cf1964d0e7c4be692df2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="ef022-102">IHostSecurityManager::GetSecurityContext Metodu</span><span class="sxs-lookup"><span data-stu-id="ef022-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="ef022-103">İstenen alır [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) ana bilgisayardan.</span><span class="sxs-lookup"><span data-stu-id="ef022-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef022-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef022-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef022-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef022-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="ef022-106">[in] Aşağıdakilerden birini [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) dönmek için güvenlik bağlamı türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="ef022-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="ef022-107">[out] Bir arabirim işaretçisi adresini `IHostSecurityContext` , `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="ef022-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef022-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ef022-108">Return Value</span></span>  
  
|<span data-ttu-id="ef022-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef022-109">HRESULT</span></span>|<span data-ttu-id="ef022-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef022-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef022-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef022-111">S_OK</span></span>|<span data-ttu-id="ef022-112">`GetSecurityContext`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ef022-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="ef022-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef022-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef022-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ef022-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef022-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef022-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef022-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ef022-116">The call timed out.</span></span>|  
|<span data-ttu-id="ef022-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef022-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef022-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="ef022-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef022-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef022-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef022-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="ef022-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef022-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef022-121">E_FAIL</span></span>|<span data-ttu-id="ef022-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ef022-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef022-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ef022-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef022-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef022-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef022-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef022-125">Remarks</span></span>  
 <span data-ttu-id="ef022-126">Bir ana iş parçacığı belirteçleri tüm kod erişimi CLR ve kullanıcı kodu tarafından kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef022-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="ef022-127">Bu tam güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemleri veya kısıtlı kod erişimi olan kod noktaları üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ef022-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="ef022-128">`IHostSecurityContext`CLR opak bu güvenlik bağlamı bilgileri yalıtır.</span><span class="sxs-lookup"><span data-stu-id="ef022-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="ef022-129">CLR bu bilgilerini yakalar ve iş parçacığı havuzu çalışan öğesi gönderme, sonlandırıcıyı yürütme ve modülü ve sınıfı oluşturma arasında taşır.</span><span class="sxs-lookup"><span data-stu-id="ef022-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef022-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef022-130">Requirements</span></span>  
 <span data-ttu-id="ef022-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef022-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef022-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef022-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef022-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ef022-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef022-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef022-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef022-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef022-135">See Also</span></span>  
 [<span data-ttu-id="ef022-136">EContextType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ef022-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="ef022-137">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef022-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="ef022-138">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef022-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

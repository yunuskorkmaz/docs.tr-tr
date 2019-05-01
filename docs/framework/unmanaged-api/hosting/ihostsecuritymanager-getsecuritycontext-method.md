---
title: IHostSecurityManager::GetSecurityContext Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f4f923e868b72e9de33884e4814ebfa329a16e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992946"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="b5032-102">IHostSecurityManager::GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5032-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="b5032-103">İstenen alır [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) konaktan.</span><span class="sxs-lookup"><span data-stu-id="b5032-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5032-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5032-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5032-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5032-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="b5032-106">[in] Aşağıdakilerden birini [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) döndürmek için güvenlik bağlamı türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="b5032-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="b5032-107">[out] Bir arabirim işaretçisine adresini `IHostSecurityContext` , `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="b5032-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5032-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b5032-108">Return Value</span></span>  
  
|<span data-ttu-id="b5032-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5032-109">HRESULT</span></span>|<span data-ttu-id="b5032-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5032-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5032-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5032-111">S_OK</span></span>|<span data-ttu-id="b5032-112">`GetSecurityContext` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b5032-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="b5032-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5032-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5032-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="b5032-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b5032-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5032-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5032-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b5032-116">The call timed out.</span></span>|  
|<span data-ttu-id="b5032-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5032-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5032-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b5032-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5032-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5032-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5032-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b5032-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5032-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5032-121">E_FAIL</span></span>|<span data-ttu-id="b5032-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b5032-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5032-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b5032-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5032-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b5032-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5032-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5032-125">Remarks</span></span>  
 <span data-ttu-id="b5032-126">Bir konak CLR ve kullanıcı kodu tarafından iş parçacığı belirteçleri tüm kod erişimi denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5032-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="b5032-127">Bu eksiksiz güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemler veya kod noktaları kod kısıtlı erişimle üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b5032-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="b5032-128">`IHostSecurityContext` CLR için donuktur bu güvenlik bağlamı bilgileri yalıtır.</span><span class="sxs-lookup"><span data-stu-id="b5032-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="b5032-129">CLR, bu bilgileri yakalar ve iş parçacığı havuzu alt öğe gönderme, sonlandırıcı yürütme ve modülü ve sınıfı oluşturma arasında taşır.</span><span class="sxs-lookup"><span data-stu-id="b5032-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5032-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5032-130">Requirements</span></span>  
 <span data-ttu-id="b5032-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5032-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5032-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b5032-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5032-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b5032-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5032-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5032-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5032-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5032-135">See also</span></span>

- [<span data-ttu-id="b5032-136">EContextType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b5032-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="b5032-137">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5032-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="b5032-138">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5032-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

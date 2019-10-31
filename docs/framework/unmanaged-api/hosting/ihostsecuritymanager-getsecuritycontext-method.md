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
ms.openlocfilehash: 66aab8081a5cce8c5ba986470bc91eb0604781a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121509"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="e7426-102">IHostSecurityManager::GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7426-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="e7426-103">Konaktan istenen [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e7426-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7426-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7426-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7426-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7426-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="e7426-106">'ndaki Ne tür güvenlik bağlamının dönebileceğini gösteren [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="e7426-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="e7426-107">dışı `eContextType``IHostSecurityContext` bir arabirim işaretçisinin adresi.</span><span class="sxs-lookup"><span data-stu-id="e7426-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7426-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e7426-108">Return Value</span></span>  
  
|<span data-ttu-id="e7426-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7426-109">HRESULT</span></span>|<span data-ttu-id="e7426-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7426-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7426-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7426-111">S_OK</span></span>|<span data-ttu-id="e7426-112">`GetSecurityContext` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e7426-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="e7426-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e7426-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e7426-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e7426-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e7426-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e7426-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e7426-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e7426-116">The call timed out.</span></span>|  
|<span data-ttu-id="e7426-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7426-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e7426-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e7426-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e7426-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e7426-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e7426-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e7426-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e7426-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="e7426-121">E_FAIL</span></span>|<span data-ttu-id="e7426-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e7426-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e7426-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e7426-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e7426-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7426-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7426-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7426-125">Remarks</span></span>  
 <span data-ttu-id="e7426-126">Bir konak, iş parçacığı belirteçlerine yönelik tüm kod erişimini CLR ve Kullanıcı koduna göre denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e7426-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="e7426-127">Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7426-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="e7426-128">`IHostSecurityContext`, CLR 'ye opak olan bu güvenlik bağlamı bilgilerini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="e7426-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="e7426-129">CLR bu bilgileri yakalar ve iş parçacığı havuzu çalışan öğesi gönderimi, sonlandırıcısı yürütmesi ve modül ve sınıf oluşturma arasında gider.</span><span class="sxs-lookup"><span data-stu-id="e7426-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7426-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7426-130">Requirements</span></span>  
 <span data-ttu-id="e7426-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7426-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7426-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e7426-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7426-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e7426-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7426-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7426-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7426-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7426-135">See also</span></span>

- [<span data-ttu-id="e7426-136">EContextType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e7426-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="e7426-137">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7426-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="e7426-138">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7426-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

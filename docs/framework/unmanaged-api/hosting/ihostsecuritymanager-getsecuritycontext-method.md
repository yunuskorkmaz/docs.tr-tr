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
ms.openlocfilehash: 7198698edce48546c4f9a82ace18d5a6e71891ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176259"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="aad35-102">IHostSecurityManager::GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aad35-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="aad35-103">İstenen [IHostSecurityContext'ı](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) ana bilgisayardan alır.</span><span class="sxs-lookup"><span data-stu-id="aad35-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aad35-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aad35-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aad35-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="aad35-106">[içinde] Ne tür bir güvenlik bağlamının döndürüleceklerini belirten [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="aad35-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="aad35-107">[çıkış] Bir arabirim işaretçisinin `IHostSecurityContext` `eContextType`adresi.</span><span class="sxs-lookup"><span data-stu-id="aad35-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aad35-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aad35-108">Return Value</span></span>  
  
|<span data-ttu-id="aad35-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aad35-109">HRESULT</span></span>|<span data-ttu-id="aad35-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aad35-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aad35-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aad35-111">S_OK</span></span>|<span data-ttu-id="aad35-112">`GetSecurityContext`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="aad35-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="aad35-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aad35-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aad35-114">Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="aad35-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aad35-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aad35-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aad35-116">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="aad35-116">The call timed out.</span></span>|  
|<span data-ttu-id="aad35-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aad35-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aad35-118">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="aad35-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aad35-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aad35-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aad35-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="aad35-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aad35-121">E_faıl</span><span class="sxs-lookup"><span data-stu-id="aad35-121">E_FAIL</span></span>|<span data-ttu-id="aad35-122">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="aad35-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aad35-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aad35-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aad35-124">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="aad35-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aad35-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aad35-125">Remarks</span></span>  
 <span data-ttu-id="aad35-126">Ana bilgisayar, iş parçacığı belirteçlerine tüm kod erişimini hem CLR hem de kullanıcı kodu yla denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="aad35-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="aad35-127">Ayrıca, tam güvenlik bağlamı bilgilerinin eşzamanlı işlemler veya sınırlı kod erişimine sahip kod noktaları arasında aktarılmasını da sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="aad35-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="aad35-128">`IHostSecurityContext`CLR'ye opak olan bu güvenlik bağlamı bilgilerini saklar.</span><span class="sxs-lookup"><span data-stu-id="aad35-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="aad35-129">CLR bu bilgileri yakalar ve iş parçacığı havuzu alt öğe gönderme, sonlandırıcı yürütme ve modül ve sınıf yapısı arasında taşır.</span><span class="sxs-lookup"><span data-stu-id="aad35-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aad35-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aad35-130">Requirements</span></span>  
 <span data-ttu-id="aad35-131">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aad35-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aad35-132">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aad35-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aad35-133">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="aad35-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aad35-134">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aad35-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad35-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aad35-135">See also</span></span>

- [<span data-ttu-id="aad35-136">EContextType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="aad35-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="aad35-137">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aad35-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="aad35-138">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aad35-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

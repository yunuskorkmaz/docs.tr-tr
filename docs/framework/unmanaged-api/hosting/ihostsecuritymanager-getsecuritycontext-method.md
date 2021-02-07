---
description: ': IHostSecurityManager:: GetSecurityContext Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0dc9e0380d2fb218b68f6beb85fa1ccba8826d85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671572"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="2d430-103">IHostSecurityManager::GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d430-103">IHostSecurityManager::GetSecurityContext Method</span></span>

<span data-ttu-id="2d430-104">Konaktan istenen [IHostSecurityContext](ihostsecuritycontext-interface.md) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="2d430-104">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d430-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d430-105">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d430-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d430-106">Parameters</span></span>  

 `eContextType`  
 <span data-ttu-id="2d430-107">'ndaki Ne tür güvenlik bağlamının dönebileceğini gösteren [EContextType](econtexttype-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="2d430-107">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="2d430-108">dışı İçin bir arabirim işaretçisinin adresi `IHostSecurityContext` `eContextType` .</span><span class="sxs-lookup"><span data-stu-id="2d430-108">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d430-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d430-109">Return Value</span></span>  
  
|<span data-ttu-id="2d430-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d430-110">HRESULT</span></span>|<span data-ttu-id="2d430-111">Description</span><span class="sxs-lookup"><span data-stu-id="2d430-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d430-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d430-112">S_OK</span></span>|<span data-ttu-id="2d430-113">`GetSecurityContext` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2d430-113">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="2d430-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d430-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d430-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2d430-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d430-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d430-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d430-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2d430-117">The call timed out.</span></span>|  
|<span data-ttu-id="2d430-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d430-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d430-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2d430-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d430-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d430-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d430-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2d430-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d430-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d430-122">E_FAIL</span></span>|<span data-ttu-id="2d430-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2d430-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d430-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2d430-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d430-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d430-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d430-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d430-126">Remarks</span></span>  

 <span data-ttu-id="2d430-127">Bir konak, iş parçacığı belirteçlerine yönelik tüm kod erişimini CLR ve Kullanıcı koduna göre denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="2d430-127">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="2d430-128">Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d430-128">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="2d430-129">`IHostSecurityContext` CLR için donuk olan bu güvenlik bağlamı bilgilerini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="2d430-129">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="2d430-130">CLR bu bilgileri yakalar ve iş parçacığı havuzu çalışan öğesi gönderimi, sonlandırıcısı yürütmesi ve modül ve sınıf oluşturma arasında gider.</span><span class="sxs-lookup"><span data-stu-id="2d430-130">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d430-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d430-131">Requirements</span></span>  

 <span data-ttu-id="2d430-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d430-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d430-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2d430-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d430-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2d430-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d430-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d430-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d430-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d430-136">See also</span></span>

- [<span data-ttu-id="2d430-137">EContextType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2d430-137">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="2d430-138">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d430-138">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="2d430-139">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d430-139">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)

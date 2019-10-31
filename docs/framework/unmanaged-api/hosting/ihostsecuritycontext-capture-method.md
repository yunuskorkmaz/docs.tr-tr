---
title: IHostSecurityContext::Capture Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
ms.openlocfilehash: 96bb3a530bf4c63c3662ecfa635a929381fc0de6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121532"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="192f8-102">IHostSecurityContext::Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="192f8-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="192f8-103">[IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)çağrısından döndürülen [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) örneğinin bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="192f8-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="192f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="192f8-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="192f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="192f8-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="192f8-106">dışı Yakalanacak `IHostSecurityContext` nesnesinin bir kopyasının adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="192f8-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="192f8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="192f8-107">Return Value</span></span>  
  
|<span data-ttu-id="192f8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="192f8-108">HRESULT</span></span>|<span data-ttu-id="192f8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="192f8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="192f8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="192f8-110">S_OK</span></span>|<span data-ttu-id="192f8-111">`Capture` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="192f8-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="192f8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="192f8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="192f8-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="192f8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="192f8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="192f8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="192f8-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="192f8-115">The call timed out.</span></span>|  
|<span data-ttu-id="192f8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="192f8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="192f8-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="192f8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="192f8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="192f8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="192f8-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="192f8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="192f8-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="192f8-120">E_FAIL</span></span>|<span data-ttu-id="192f8-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="192f8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="192f8-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="192f8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="192f8-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="192f8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="192f8-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="192f8-124">Remarks</span></span>  
 <span data-ttu-id="192f8-125">`Capture` döndürülen arabirim işaretçisi yakalanan bağlamın bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="192f8-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="192f8-126">Bu bilgiler zaman uyumsuz bir kod noktasına taşındığında, yaşam süresi Çağrının yapıldığı işaretçiden bu yana karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="192f8-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="192f8-127">Bu nedenle özgün işaretçi serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="192f8-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="192f8-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="192f8-128">Requirements</span></span>  
 <span data-ttu-id="192f8-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="192f8-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="192f8-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="192f8-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="192f8-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="192f8-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="192f8-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="192f8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192f8-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="192f8-133">See also</span></span>

- [<span data-ttu-id="192f8-134">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="192f8-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="192f8-135">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="192f8-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

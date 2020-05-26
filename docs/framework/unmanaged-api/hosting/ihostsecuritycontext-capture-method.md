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
ms.openlocfilehash: 40857620e47befce361ff8cb04af527915051df3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804205"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="69664-102">IHostSecurityContext::Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69664-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="69664-103">[IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)çağrısından döndürülen [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) örneğinin bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="69664-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69664-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="69664-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69664-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69664-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="69664-106">dışı Yakalanacak nesnenin bir kopyasının adresine yönelik bir işaretçi `IHostSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="69664-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69664-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69664-107">Return Value</span></span>  
  
|<span data-ttu-id="69664-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="69664-108">HRESULT</span></span>|<span data-ttu-id="69664-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69664-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69664-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="69664-110">S_OK</span></span>|<span data-ttu-id="69664-111">`Capture`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="69664-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="69664-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="69664-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="69664-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="69664-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="69664-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="69664-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="69664-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="69664-115">The call timed out.</span></span>|  
|<span data-ttu-id="69664-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="69664-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="69664-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="69664-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="69664-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="69664-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="69664-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="69664-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="69664-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="69664-120">E_FAIL</span></span>|<span data-ttu-id="69664-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="69664-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="69664-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="69664-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="69664-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="69664-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69664-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69664-124">Remarks</span></span>  
 <span data-ttu-id="69664-125">Öğesinden döndürülen arabirim işaretçisi, `Capture` yakalanan bağlamın bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="69664-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="69664-126">Bu bilgiler zaman uyumsuz bir kod noktasına taşındığında, yaşam süresi Çağrının yapıldığı işaretçiden bu yana karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="69664-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="69664-127">Bu nedenle özgün işaretçi serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="69664-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69664-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69664-128">Requirements</span></span>  
 <span data-ttu-id="69664-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69664-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69664-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="69664-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69664-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="69664-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69664-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69664-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69664-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69664-133">See also</span></span>

- [<span data-ttu-id="69664-134">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69664-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="69664-135">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69664-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
